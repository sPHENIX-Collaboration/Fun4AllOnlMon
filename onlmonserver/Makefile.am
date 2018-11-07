AUTOMAKE_OPTIONS = foreign

BUILT_SOURCES = \
  testexternals.cc

AM_CPPFLAGS = \
  -I$(includedir) \
  -I$(OFFLINE_MAIN)/include \
  -I$(ROOTSYS)/include \
  -I$(OPT_SPHENIX)/include

pkginclude_HEADERS = \
  OnlMonServer.h 

noinst_HEADERS = \
  OnlMonServerLinkDef.h 

lib_LTLIBRARIES = \
  libonlmonserver.la

libonlmonserver_la_SOURCES = \
  HistoServer.cc \
  OnlMonServer.cc \
  OnlMonServer_Dict.cc 

nodist_libfun4all_la_SOURCES = OnlMonServer_Dict.cc

libonlmonserver_la_LIBADD = \
  -L$(libdir) \
  -L$(OFFLINE_MAIN)/lib \
  -lfun4all

noinst_PROGRAMS = \
  testexternals

testexternals_SOURCES = testexternals.cc
testexternals_LDADD   = libonlmonserver.la

testexternals.cc:
	echo "//*** this is a generated file. Do not commit, do not edit" > $@
	echo "int main()" >> $@
	echo "{" >> $@
	echo "  return 0;" >> $@
	echo "}" >> $@

# Rule for generating table CINT dictionaries.
%_Dict.cc: %.h %LinkDef.h
	rootcint -f $@ @CINTDEFS@ -c $(DEFAULT_INCLUDES) $(AM_CPPFLAGS) $^

clean-local:
	rm -f *Dict*
