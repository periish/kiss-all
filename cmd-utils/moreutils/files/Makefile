BINS=isutf8 ifdata ifne pee sponge mispipe lckdo parallel errno
PERLSCRIPTS=vidir vipe ts combine zrun chronic
CFLAGS?=-O2 -g -Wall
INSTALL_BIN?=install -s
PREFIX?=/usr

all: $(BINS)

isutf8: is_utf8/*.c is_utf8/*.h
		$(MAKE) -C is_utf8/
		cp is_utf8/isutf8 .

install:
		mkdir -p $(DESTDIR)$(PREFIX)/bin
		$(INSTALL_BIN) $(BINS) $(DESTDIR)$(PREFIX)/bin
		install $(PERLSCRIPTS) $(DESTDIR)$(PREFIX)/bin

errno.o: errnos.h
errnos.h:
		echo '#include <errno.h>' > dump.c
		$(CC) -E -dD dump.c | awk '/^#define E/ { printf "{\"%s\",%s},\n", $$2, $$2 }' > errnos.h
		rm -f dump.c
