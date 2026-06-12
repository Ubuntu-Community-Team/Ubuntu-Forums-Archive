---
title: "fortran and more for ubuntu!!! [ at Christmas]"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by lgcovizzi on 2010-12-10
Dears!

I need to install the tools for C, etc ... (for the program FFTW Version 3.2.2 on [http://www.fftw.org/](http://www.fftw.org/))
See the report below! 

How do I make the installation of these dependencies on ubuntu?
```

lg@pc:~/Downloads/fttw/fftw-3.2.2$ sudo ./configurechecking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for C compiler vendor... gnu
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for ocamlc... ocamlc
checking for ocamlopt... ocamlopt
checking for ocamldep... ocamldep
checking whether C compiler accepts -malign-double... yes
checking whether C compiler accepts -fstrict-aliasing... yes
checking whether C compiler accepts -ffast-math... yes
checking for gcc architecture flag... 
checking for x86 cpuid 0 output... a:756e6547:6c65746e:49656e69
checking for x86 cpuid 1 output... 6fb:1040800:e3bd:bfebfbff
checking whether C compiler accepts -march=core2... yes
checking for gcc architecture flag... -march=core2
checking whether C compiler accepts -O3 -fomit-frame-pointer -malign-double -fstrict-aliasing -ffast-math -march=core2... yes
checking whether C compiler accepts -fno-schedule-insns... yes
checking whether C compiler accepts -fno-web... yes
checking whether C compiler accepts -fno-loop-optimize... yes
checking whether C compiler accepts --param inline-unit-growth=1000... yes
checking whether C compiler accepts --param large-function-growth=1000... yes
checking for ANSI C header files... (cached) yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking c_asm.h usability... no
checking c_asm.h presence... no
checking for c_asm.h... no
checking intrinsics.h usability... no
checking intrinsics.h presence... no
checking for intrinsics.h... no
checking for stdint.h... (cached) yes
checking mach/mach_time.h usability... no
checking mach/mach_time.h presence... no
checking for mach/mach_time.h... no
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking xmmintrin.h usability... yes
checking xmmintrin.h presence... no
configure: WARNING: xmmintrin.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: xmmintrin.h: proceeding with the compiler's result
checking for xmmintrin.h... yes
checking altivec.h usability... no
checking altivec.h presence... no
checking for altivec.h... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for long double... yes
checking for hrtime_t... no
checking size of int... 4
checking size of unsigned int... 4
checking size of long... 4
checking size of unsigned long... 4
checking size of long long... 8
checking size of unsigned long long... 8
checking size of size_t... 4
checking size of ptrdiff_t... 4
checking for uintptr_t... yes
checking size of float... 4
checking size of double... 8
checking for working alloca.h... yes
checking for alloca... yes
checking for working strtod... yes
checking for vprintf... yes
checking for _doprnt... no
checking for sin in -lm... yes
checking for BSDgettimeofday... no
checking for gettimeofday... yes
checking for gethrtime... no
checking for read_real_time... no
checking for time_base_to_time... no
checking for drand48... yes
checking for sqrt... yes
checking for memset... yes
checking for posix_memalign... yes
checking for memalign... yes
checking for _mm_malloc... no
checking for _mm_free... no
checking for clock_gettime... no
checking for mach_absolute_time... no
checking for sysctl... yes
checking for abort... yes
checking for sinl... yes
checking for cosl... yes
checking for snprintf... yes
checking whether drand48 is declared... yes
checking whether memalign is declared... no
checking whether posix_memalign is declared... yes
checking whether sinl is declared... no
checking whether cosl is declared... no
checking for _rtc intrinsic... no
checking for isnan... yes
checking whether C compiler accepts -mpreferred-stack-boundary=4... yes
checking whether the stack is at least 8-byte aligned by gcc... checking whether C compiler accepts -malign-double... (cached) yes
yes
checking for g77... no
checking for xlf... no
checking for f77... f77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether f77 accepts -g... yes
checking whether we are using the GNU Fortran 77 compiler... (cached) yes
checking whether f77 accepts -g... (cached) yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for f77 option to produce PIC... -fPIC
checking if f77 PIC flag -fPIC works... yes
checking if f77 static flag -static works... yes
checking if f77 supports -c -o file.o... yes
checking if f77 supports -c -o file.o... (cached) yes
checking whether the f77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking how to get verbose linking output from f77... configure: WARNING: cannot determine how to obtain linking information from f77

checking for Fortran 77 libraries of f77... 
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... lower case, underscore, extra underscore
checking whether a cycle counter is available... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating support/Makefile
config.status: creating genfft/Makefile
config.status: creating kernel/Makefile
config.status: creating simd/Makefile
config.status: creating simd/nonportable/Makefile
config.status: creating dft/Makefile
config.status: creating dft/scalar/Makefile
config.status: creating dft/scalar/codelets/Makefile
config.status: creating dft/simd/Makefile
config.status: creating dft/simd/codelets/Makefile
config.status: creating rdft/Makefile
config.status: creating rdft/scalar/Makefile
config.status: creating rdft/scalar/r2cf/Makefile
config.status: creating rdft/scalar/r2cb/Makefile
config.status: creating rdft/scalar/r2r/Makefile
config.status: creating rdft/simd/Makefile
config.status: creating rdft/simd/codelets/Makefile
config.status: creating reodft/Makefile
config.status: creating threads/Makefile
config.status: creating cell/Makefile
config.status: creating cell/spu/Makefile
config.status: creating api/Makefile
config.status: creating libbench2/Makefile
config.status: creating tests/Makefile
config.status: creating doc/Makefile
config.status: creating doc/FAQ/Makefile
config.status: creating tools/Makefile
config.status: creating tools/fftw_wisdom.1
config.status: creating tools/fftw-wisdom-to-conf
config.status: creating m4/Makefile
config.status: creating fftw.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
lg@pc:~/Downloads/fttw/fftw-3.2.2$ sudo aptitude install fortran77-compiler 
Nenhum pacote será instalado, atualizado ou removido.
0 pacotes atualizados, 0 novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso obter 0B de arquivos. Depois do desempacotamento, 0B serão usados.
                                             
lg@pc:~/Downloads/fttw/fftw-3.2.2$ clear

lg@pc:~/Downloads/fttw/fftw-3.2.2$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for C compiler vendor... gnu
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for ocamlc... ocamlc
checking for ocamlopt... ocamlopt
checking for ocamldep... ocamldep
checking whether C compiler accepts -malign-double... yes
checking whether C compiler accepts -fstrict-aliasing... yes
checking whether C compiler accepts -ffast-math... yes
checking for gcc architecture flag... 
checking for x86 cpuid 0 output... a:756e6547:6c65746e:49656e69
checking for x86 cpuid 1 output... 6fb:1040800:e3bd:bfebfbff
checking whether C compiler accepts -march=core2... yes
checking for gcc architecture flag... -march=core2
checking whether C compiler accepts -O3 -fomit-frame-pointer -malign-double -fstrict-aliasing -ffast-math -march=core2... yes
checking whether C compiler accepts -fno-schedule-insns... yes
checking whether C compiler accepts -fno-web... yes
checking whether C compiler accepts -fno-loop-optimize... yes
checking whether C compiler accepts --param inline-unit-growth=1000... yes
checking whether C compiler accepts --param large-function-growth=1000... yes
checking for ANSI C header files... (cached) yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking c_asm.h usability... no
checking c_asm.h presence... no
checking for c_asm.h... no
checking intrinsics.h usability... no
checking intrinsics.h presence... no
checking for intrinsics.h... no
checking for stdint.h... (cached) yes
checking mach/mach_time.h usability... no
checking mach/mach_time.h presence... no
checking for mach/mach_time.h... no
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking xmmintrin.h usability... yes
checking xmmintrin.h presence... no
configure: WARNING: xmmintrin.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: xmmintrin.h: proceeding with the compiler's result
checking for xmmintrin.h... yes
checking altivec.h usability... no
checking altivec.h presence... no
checking for altivec.h... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for long double... yes
checking for hrtime_t... no
checking size of int... 4
checking size of unsigned int... 4
checking size of long... 4
checking size of unsigned long... 4
checking size of long long... 8
checking size of unsigned long long... 8
checking size of size_t... 4
checking size of ptrdiff_t... 4
checking for uintptr_t... yes
checking size of float... 4
checking size of double... 8
checking for working alloca.h... yes
checking for alloca... yes
checking for working strtod... yes
checking for vprintf... yes
checking for _doprnt... no
checking for sin in -lm... yes
checking for BSDgettimeofday... no
checking for gettimeofday... yes
checking for gethrtime... no
checking for read_real_time... no
checking for time_base_to_time... no
checking for drand48... yes
checking for sqrt... yes
checking for memset... yes
checking for posix_memalign... yes
checking for memalign... yes
checking for _mm_malloc... no
checking for _mm_free... no
checking for clock_gettime... no
checking for mach_absolute_time... no
checking for sysctl... yes
checking for abort... yes
checking for sinl... yes
checking for cosl... yes
checking for snprintf... yes
checking whether drand48 is declared... yes
checking whether memalign is declared... no
checking whether posix_memalign is declared... yes
checking whether sinl is declared... no
checking whether cosl is declared... no
checking for _rtc intrinsic... no
checking for isnan... yes
checking whether C compiler accepts -mpreferred-stack-boundary=4... yes
checking whether the stack is at least 8-byte aligned by gcc... checking whether C compiler accepts -malign-double... (cached) yes
yes
checking for g77... no
checking for xlf... no
checking for f77... f77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether f77 accepts -g... yes
checking whether we are using the GNU Fortran 77 compiler... (cached) yes
checking whether f77 accepts -g... (cached) yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for f77 option to produce PIC... -fPIC
checking if f77 PIC flag -fPIC works... yes
checking if f77 static flag -static works... yes
checking if f77 supports -c -o file.o... yes
checking if f77 supports -c -o file.o... (cached) yes
checking whether the f77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking how to get verbose linking output from f77... configure: WARNING: cannot determine how to obtain linking information from f77

checking for Fortran 77 libraries of f77... 
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... lower case, underscore, extra underscore
checking whether a cycle counter is available... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating support/Makefile
config.status: creating genfft/Makefile
config.status: creating kernel/Makefile
config.status: creating simd/Makefile
config.status: creating simd/nonportable/Makefile
config.status: creating dft/Makefile
config.status: creating dft/scalar/Makefile
config.status: creating dft/scalar/codelets/Makefile
config.status: creating dft/simd/Makefile
config.status: creating dft/simd/codelets/Makefile
config.status: creating rdft/Makefile
config.status: creating rdft/scalar/Makefile
config.status: creating rdft/scalar/r2cf/Makefile
config.status: creating rdft/scalar/r2cb/Makefile
config.status: creating rdft/scalar/r2r/Makefile
config.status: creating rdft/simd/Makefile
config.status: creating rdft/simd/codelets/Makefile
config.status: creating reodft/Makefile
config.status: creating threads/Makefile
config.status: creating cell/Makefile
config.status: creating cell/spu/Makefile
config.status: creating api/Makefile
config.status: creating libbench2/Makefile
config.status: creating tests/Makefile
config.status: creating doc/Makefile
config.status: creating doc/FAQ/Makefile
config.status: creating tools/Makefile
config.status: creating tools/fftw_wisdom.1
config.status: creating tools/fftw-wisdom-to-conf
config.status: creating m4/Makefile
config.status: creating fftw.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
lg@pc:~/Downloads/fttw/fftw-3.2.2$
```

---

### Post by lykeion on 2010-12-10
Please enclose terminal output in CODE tags using the # button for readability.

1. You don't need to use sudo for **configure**
2. After configure is done (you can ignore the Fortran warnings) you should compile it with **make**.
3. Finally install it with **sudo make install**, or you can create a debian package using **sudo checkinstall**

All this is explained in the online manual [here]("http://www.fftw.org/fftw3_doc/Installation-on-Unix.html#Installation-on-Unix"). Have you actually read it? 
There you could also read that there already are debian packages for the latest version of fftw3, so there shouldn't be any need to compile your own binaries.

In Ubuntu you can easily install fftw from the repositories. Start Synaptic or Ubuntu Software Center and search for "fftw3".

---

