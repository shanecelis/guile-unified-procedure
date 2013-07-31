include $(top_srcdir)/support/automake/noweb.am
include $(top_srcdir)/support/automake/guile.am

.SECONDARY:

NOWEAVE_FLAGS = -n -delay
BUILT_SOURCES = $(NOWEB_BUILT_FILES) unified-procedure.c.x 
CLEANFILES = $(NOWEB_CLEANFILES) unified-procedure.c.x 

WARN_NOTANGLE = $(top_builddir)/bin/warn-notangle

dist-hook:
	cp $(distdir)/*.pdf $(top_distdir)

NOWEB_DOCS = unified-procedure-doc.pdf 
NOWEB_FILES = unified-procedure.nw unified-procedure-doc.nw
NOWEB_PRODUCTS = unified-procedure.c unified-procedure.h unified-procedure.scm unified-procedure-test.c unified-procedure-test.scm
EXTRA_DIST = $(NOWEB_DOCS) $(NOWEB_EXTRA_DIST)

unified-procedure-doc.pdf : unified-procedure.tex unified-procedure-doc.tex

unified-procedure.o : unified-procedure.c.x

check_PROGRAMS = unified-procedure-test-c

TESTS = unified-procedure-test-c unified-procedure-test.scm
TEST_EXTENSIONS = .scm 
SCM_LOG_COMPILER = $(ENV) guile 

lib_LTLIBRARIES = libguile-unified-procedure.la

guilemoduledir = $(prefix)/share/guile/site/
dist_guilemodule_DATA = unified-procedure.scm unified-procedure.go

AM_CFLAGS  = $(GUILE_CFLAGS)
unified_procedure_test_c_LDADD   = $(GUILE_LIBS) libguile-unified-procedure.la
unified_procedure_test_c_LDFLAGS = $(GUILE_LDFLAGS)
unified_procedure_test_c_SOURCES = unified-procedure-test.c

libguile_unified_procedure_la_LIBADD  = $(GUILE_LIBS)
libguile_unified_procedure_la_SOURCES = unified-procedure.c
include_HEADERS = unified-procedure.h 

MAINTAINERCLEANFILES = Makefile.in config.h.in 
