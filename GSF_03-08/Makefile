
$(info $(_InputFile) running under $(_System).)



PREFIX        = gsf
ARCH          = $(shell uname -m)
VERSION       = 03.08
TGT           = lib$(PREFIX)-$(ARCH)-$(VERSION).so
STATIC_TGT    = lib$(PREFIX).a
MACROS        = -DLINUX -DUNIX -DDISPLAY_SPINNER -D_LARGEFILE64_SOURCE
CFLAGS        = $(MACROS) -fPIC -Wall -D_STRICT_ANSI -D_LARGEFILE64_SOURCE
CPPFLAGS      = $(CFLAGS)
LFLAGS        = -shared $(LINK_FLAGS)
CC            = gcc
CPP           = gcc
LINKER        = gcc
STATIC_LINKER = ar
AR            = ar
RM            = rm -f
LIBS          = -lwsock32

.cpp.o:
	$(CPP) -c $(CPPFLAGS) $*.cpp -o$@
.c.o:
	$(CC) -c $(CFLAGS) $*.c -o$@

OBJS = gsf.o gsf_enc.o gsf_dec.o gsf_indx.o gsf_info.o gsf_geo.o

all : $(OBJS)
	$(LINKER) $(LFLAGS) -o $(TGT) $(OBJS)
	$(STATIC_LINKER) rcs $(STATIC_TGT) $(OBJS)

clean:
	$(RM) $(TGT) $(STATIC_TGT) $(OBJS) 

