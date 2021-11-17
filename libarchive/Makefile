CFLAGS     = -g 
INCLUDE    = -I/usr/include -I.
LIBS       = -larchive

PYVER ?= 3.9

all: __libarchive.so

_libarchive_wrap.c: _libarchive.i
	#swig -python -c++ -Wall -shadow _libarchive.i
	swig -python -Wall -shadow _libarchive.i

_libarchive_wrap.o: _libarchive_wrap.c
	${CC} -c ${CFLAGS} -fPIC ${INCLUDE} $$(python${PYVER}-config --cflags) _libarchive_wrap.c

__libarchive.so: _libarchive_wrap.o
	${CC} _libarchive_wrap.o -shared $$(python${PYVER}-config --ldflags) -o __libarchive.so ${LIBS}

clean:
	rm -f *.o *.so *.pyc
