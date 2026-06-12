---
title: "Canon MF6530 problems"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by blk03mitsues on 2009-08-11
As title says i got a canon imageClass mf6530 which is the only reason i need to keep switching back and forth with Vista. today i made my mind and decided to get the freaking things installed.my 8 hour shift is almost up and i freaking give up.

so i downloaded the needed UFRII driver. cups installs it but it says Printer is missing program pstoutfr2cpac. so i try the following instructions in the folder

> bvc@BVC-desktop:~/Desktop/UFR_II_Printer_Driver_for_Linux_Src_V180_uk_EN/Sources/cndrvcups-lb-1.80/pstoufr2cpca$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for main in -lbuftool... no
checking for main in -lcups... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for dup2... yes
checking for memset... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating filter/Makefile
config.status: creating config.h
config.status: executing depfiles commands
bvc@BVC-desktop:~/Desktop/UFR_II_Printer_Driver_for_Linux_Src_V180_uk_EN/Sources/cndrvcups-lb-1.80/pstoufr2cpca$ make
make  all-recursive
make[1]: Entering directory `/home/bvc/Desktop/UFR_II_Printer_Driver_for_Linux_Src_V180_uk_EN/Sources/cndrvcups-lb-1.80/pstoufr2cpca'
Making all in filter
make[2]: Entering directory `/home/bvc/Desktop/UFR_II_Printer_Driver_for_Linux_Src_V180_uk_EN/Sources/cndrvcups-lb-1.80/pstoufr2cpca/filter'
gcc -DHAVE_CONFIG_H -I. -I..    -O2 -Wall -fPIC -g -O2 -MT pstoufr2cpca.o -MD -MP -MF .deps/pstoufr2cpca.Tpo -c -o pstoufr2cpca.o pstoufr2cpca.c
pstoufr2cpca.c:34:21: error: buflist.h: No such file or directory
pstoufr2cpca.c:1073: error: expected declaration specifiers or ‘...’ before ‘BufList’
pstoufr2cpca.c: In function ‘get_ps_params’:
pstoufr2cpca.c:1080: error: ‘BufList’ undeclared (first use in this function)
pstoufr2cpca.c:1080: error: (Each undeclared identifier is reported only once
pstoufr2cpca.c:1080: error: for each function it appears in.)
pstoufr2cpca.c:1080: error: ‘bl’ undeclared (first use in this function)
pstoufr2cpca.c:1081: error: ‘prev_bl’ undeclared (first use in this function)
pstoufr2cpca.c:1114: warning: implicit declaration of function ‘buflist_new’
pstoufr2cpca.c:1116: error: ‘ps_data’ undeclared (first use in this function)
pstoufr2cpca.c:1119: warning: implicit declaration of function ‘buflist_add_tail’
pstoufr2cpca.c: In function ‘main’:
pstoufr2cpca.c:1458: error: ‘BufList’ undeclared (first use in this function)
pstoufr2cpca.c:1458: error: ‘p_ps_data’ undeclared (first use in this function)
pstoufr2cpca.c:1511: error: too many arguments to function ‘get_ps_params’
pstoufr2cpca.c:1530: warning: implicit declaration of function ‘buflist_write’
pstoufr2cpca.c:1596: warning: implicit declaration of function ‘buflist_destroy’
make[2]: *** [pstoufr2cpca.o] Error 1
make[2]: Leaving directory `/home/bvc/Desktop/UFR_II_Printer_Driver_for_Linux_Src_V180_uk_EN/Sources/cndrvcups-lb-1.80/pstoufr2cpca/filter'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bvc/Desktop/UFR_II_Printer_Driver_for_Linux_Src_V180_uk_EN/Sources/cndrvcups-lb-1.80/pstoufr2cpca'
make: *** [all] Error 2
bvc@BVC-desktop:~/Desktop/UFR_II_Printer_Driver_for_Linux_Src_V180_uk_EN/Sources/cndrvcups-lb-1.80/pstoufr2cpca$ 


next i try "su" and i get "su: Authentication failure"

---

### Post by blk03mitsues on 2009-08-12
any one?

---

### Post by jserink on 2009-09-20
> **blk03mitsues said:**
> any one?
Oh dear......

su, after which you need to enter the root password. you could also try "man su"?

Cheers,
John

ubuntu is a Zulu word meaning "gentoo is too hard for me".

---

### Post by halitech on 2009-09-20
it would actually be sudo that you would need to try with the command.

---

