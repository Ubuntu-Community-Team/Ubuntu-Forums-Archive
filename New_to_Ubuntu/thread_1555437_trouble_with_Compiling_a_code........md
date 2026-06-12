---
title: "trouble with Compiling a code......."
date: 2010-08-18
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-18
Hi I am having a problem compiling my program. Here is the result of the compilation 
```

gfortran -g FDTD.o routine.o cutcell.o -lm -L/usr/lib -L. -llinpak -lblas -lstdc++ -o FDTD
/usr/bin/ld: skipping incompatible ./liblinpak.a when searching for -llinpak
/usr/bin/ld: skipping incompatible /usr/local/lib/liblinpak.a when searching for -llinpak
/usr/bin/ld: cannot find -llinpak
collect2: ld returned 1 exit status
make: *** [FDTD] Error 1
```


Here is my makefile.

```

CC = $(CXX)
#CXXFLAGS = -g -Wall
CXXFLAGS = -g

TARGETS = FDTD 

all  : $(TARGETS)

FDTD : FDTD.o routine.o cutcell.o
	gfortran -g FDTD.o routine.o cutcell.o -lm -L/usr/lib -L. -llinpak -lblas -lstdc++ -o FDTD
#	g++ -g FDTD.o routine.o cutcell.o -lm  -lgfortranbegin -L. -llinpak -lblas -lstdc++  -o FDTD

.PHONY: clean
SRCS = $(wildcard *.cpp)
OBJS = $(SRCS:.cpp=.o) 
clean:
	$(RM) $(OBJS) $(TARGETS) $(DEPS) 

# check dependencies
DEPS := $(SRCS:.cpp=.dep)

include $(DEPS)
%.dep: %.cpp
	@echo 'Generating/Updating dependency for $<'
	@/bin/sh -ec '$(CXX) -MM $(CXXFLAGS) $< \
                | sed '\''s/\(.*\)\.o[ :]*/\1.o $@ : /g'\'' > $@; \
                [ -s $@ ] || rm -f $@'

tags:
	ctags *.cpp *.h

```

---

### Post by anewguy on 2010-08-18
For whatever reason it's not finding the linpak library.  Have you installed it, and if so, to what folder?

You may have better luck with this posting it on the programming/development forum - more programmers there.

Dave ;)

---

### Post by Bachstelze on 2010-08-18
> /usr/bin/ld: skipping **incompatible** /usr/local/lib/liblinpak.a when searching for -llinpak

The library is 32-bit, and you are running 64-bit Ubuntu, or vice versa.

---

