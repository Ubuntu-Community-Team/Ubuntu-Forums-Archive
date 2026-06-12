---
title: "Emacs ate my code"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-07-07
Hey all,

I've been coding all day and I finally got my program up and running and was in the middle of debugging when my code completely disappeared. Well not completely, it was open in emacs and I made some changes and tried to compile and for some strange reason it wouldn't (probably because it didn't exist anymore). After a few failed compiles, I "saved" and exited the code hoping to re open it. I ls'ed and that's when my heart stopped, my code was completely gone. 

I tried recovering with emacs but it gives me:

```
recover-file: Auto-save file ~/Documents/SBREU/#avg.c# not current
```

Here's my terminal output before and after trying to compile (the code was called avg.c):

```
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ ls
1935-1948.txt  avg.c                hourly_wind_summer.data  threshhold.c
1948-1972.txt  daily.c              mixingdates.txt          threshhold.c~
1973-1974.txt  extractwind          summers.pl               wind_summer.data
1975-2009.txt  extractwind.c        test2.data
allwind.txt    getMixingEvents.sh   test.data
avg            getMixingEvents.sh~  threshhold
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ 
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ emacs allwind.txt &
[3] 7551
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ gedit allwind.txt 
/home/brian/.themes/Murrine Brave Dark/gtk-2.0/gtkrc:109: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
[3]+  Done                    emacs allwind.txt
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ 
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ 
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ gedit hourly_wind_summer.data 
/home/brian/.themes/Murrine Brave Dark/gtk-2.0/gtkrc:109: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ cp ../asdf.txt test.data
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ emacs test.data
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ 
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ 
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ gcc -Wall -lm -o avg.c avg
avg: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: first defined here
avg:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
avg: In function `_fini':
/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: first defined here
avg:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
avg: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.data+0x0): first defined here
avg: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o:(.data+0x0): first defined here
avg: In function `_init':
/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: first defined here
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
avg:(.dtors+0x4): first defined here
collect2: ld returned 1 exit status
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ gcc -Wall -lm -o avg.c avg
avg: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: first defined here
avg:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
avg: In function `_fini':
/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: first defined here
avg:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
avg: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.data+0x0): first defined here
avg: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o:(.data+0x0): first defined here
avg: In function `_init':
/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: first defined here
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
avg:(.dtors+0x4): first defined here
collect2: ld returned 1 exit status
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ gcc -Wall -lm -o avg.c avg
avg: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: first defined here
avg:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
avg: In function `_fini':
/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: first defined here
avg:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
avg: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.data+0x0): first defined here
avg: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o:(.data+0x0): first defined here
avg: In function `_init':
/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: first defined here
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
avg:(.dtors+0x4): first defined here
collect2: ld returned 1 exit status
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ gcc -Wall -lm -o avg.c avg
avg: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: first defined here
avg:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
avg: In function `_fini':
/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: first defined here
avg:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
avg: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.data+0x0): first defined here
avg: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o:(.data+0x0): first defined here
avg: In function `_init':
/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: first defined here
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
avg:(.dtors+0x4): first defined here
collect2: ld returned 1 exit status
[2]+  Done                    gedit mixingdates.txt
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ 
```

Please help, I really don't want to write all that code up again =/.

-SMRT

---

### Post by bostonaholic on 2009-07-07
how about

```
find . -name avg.c
```

---

### Post by Mornedhel on 2009-07-07
This is peculiar.

Are you running emacs-snapshot or emacs22 ?

---

### Post by I[AM]SMRT on 2009-07-07
Found my problem, I'm an idiot. Bah hate my life.

```
brian@brian-laptop:~/Documents/SBREU/wind_extraction$ gcc -Wall -lm **-o avg.c** avg
```

And I'm running emacs22.

---

