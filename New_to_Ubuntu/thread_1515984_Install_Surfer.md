---
title: "Install Surfer ?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by koukourikos on 2010-06-23
I cannot install Surfer.
I have downloaded from here the source files [http://www.imaginary2008.de/surfer.php?lang=en]("http://www.imaginary2008.de/surfer.php?lang=en")

I have extracted surfer-0.0.197.tar.gz and surf-for-surfer but when I'm trying to install it  according to the readme instructions the "./configure --disable-gui" command ends with errors

this is what I get 
```

./configure --disable-gui
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for AIX... no
checking for library containing strerror... none required
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for ANSI C header files... (cached) yes
checking for flex... flex
checking for flex... (cached) flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for bison... bison -y
checking for ranlib... ranlib
checking whether gcc accepts -Wall... yes
checking whether gcc accepts -W... yes
checking whether gcc accepts -Wwrite-strings... yes
checking whether gcc accepts -Wpointer-arith... yes
checking whether gcc accepts -Wconversion... yes
checking whether gcc accepts -Wno-unused... yes
checking whether gcc accepts -Wstrict-prototypes... no
checking whether gcc accepts -Wmissing-prototypes... no
checking whether gcc accepts -Wmissing-declarations... no
checking whether gcc accepts -Wnested-externs... yes
checking whether g++ supports bool... yes
checking whether g++ accepts -fno-rtti... yes
checking whether g++ accepts -fno-exceptions... yes
checking whether g++ accepts -Wall... yes
checking whether g++ accepts -W... yes
checking whether g++ accepts -Wwrite-strings... yes
checking whether g++ accepts -Wpointer-arith... yes
checking whether g++ accepts -Wconversion... yes
checking whether g++ accepts -Wno-unused... yes
checking whether g++ accepts -Wstrict-prototypes... no
checking whether g++ accepts -Wmissing-prototypes... no
checking whether g++ accepts -Woverloaded-virtual... yes
checking whether g++ accepts -Wno-deprecated... yes
checking whether g++ supports explicit template instantiation... yes
checking whether the compiler supports function templates with non-type parameters... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for main in -lpthread... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking if compilation of multithreaded programs works... yes
checking whether there is a prototype for gethostname in unistd.h... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for main in -lm... yes
checking if pow(0,0)!=1... no
checking for main in -lz... yes
checking for main in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for main in -ltiff... yes
checking for tiffio.h... no
checking tiff34/tiffio.h usability... no
checking tiff34/tiffio.h presence... no
checking for tiff34/tiffio.h... no
checking gmp.h usability... yes
checking gmp.h presence... yes
checking for gmp.h... yes
checking for main in -lgmp... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: WARNING:  src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating image-formats/Makefile
config.status: WARNING:  image-formats/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drawfunc/Makefile
config.status: WARNING:  drawfunc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating yaccsrc/Makefile
config.status: WARNING:  yaccsrc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating curve/Makefile
config.status: WARNING:  curve/Makefile.in seems to ignore the --datarootdir setting
config.status: creating mt/Makefile
config.status: WARNING:  mt/Makefile.in seems to ignore the --datarootdir setting
config.status: creating draw/Makefile
config.status: WARNING:  draw/Makefile.in seems to ignore the --datarootdir setting
config.status: creating misc/Makefile
config.status: WARNING:  misc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating debug/Makefile
config.status: WARNING:  debug/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtkgui/Makefile
config.status: WARNING:  gtkgui/Makefile.in seems to ignore the --datarootdir setting
config.status: creating dither/Makefile
config.status: WARNING:  dither/Makefile.in seems to ignore the --datarootdir setting

```

---

### Post by diesch on 2010-06-23
This aren't errors, just warnings.

---

### Post by wojox on 2010-06-23
It didn't come with any instructions to help set it up. 

Poke around in the directory and check.

---

### Post by ronnielsen1 on 2010-06-23
There's usually install instructions in a tar.gz file once you extract it (and there is in this one) There's also a java version in development that installs easier.
[http://www.imaginary-exhibition.com/data/jSurfer.zip](http://www.imaginary-exhibition.com/data/jSurfer.zip)
The java version downloads as jSurfer.zip Extract this and open a terminal
cd (to the folder jSurfer)
chmod +x Jsurfer.jar
 ./Jsurfer.jar

---

### Post by koukourikos on 2010-06-23
@diesch Yes they are warnings but if I try "make"  and "sudo make install" it gives me errors.

The java version is working thank you ronnielsen1!!

I was just wondering what  the differences between a java version and a native(Linux) version in general?( expect that java-version is cross-platform )

---

