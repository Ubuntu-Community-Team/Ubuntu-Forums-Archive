---
title: "Unable to install ecgpuwave"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by taildragger on 2010-03-24
I switched from XP to Ubuntu 9.10 a couple weeks ago.

I am trying to install a program called ecgpuwave (part of the PhysioToolkit). I followed the installation instructions found here [http://www.physionet.org/physiotools/ecgpuwave/src/INSTALL](http://www.physionet.org/physiotools/ecgpuwave/src/INSTALL) . but when i run 'make' i get the following error:

tony@ubuntu:~/Downloads/ecgpuwave-1.3$ make
f77 -g -o ecgpuwave ecgpuwave.o principal.o aldetqrs.o graf.o dades.o impregraf.o lgraf.o prosen.o int_qt.o punts.o l_impregraf.o wfdbf.o -L/usr/bin -lwfdb
principal.o: In function `impregraf_':
/home/tony/Downloads/ecgpuwave-1.3/principal.f:404: undefined reference to `lnblnk_'
/home/tony/Downloads/ecgpuwave-1.3/principal.f:404: undefined reference to `lnblnk_'
/home/tony/Downloads/ecgpuwave-1.3/principal.f:410: undefined reference to `lnblnk_'
/home/tony/Downloads/ecgpuwave-1.3/principal.f:410: undefined reference to `lnblnk_'
/home/tony/Downloads/ecgpuwave-1.3/principal.f:413: undefined reference to `lnblnk_'
principal.o:/home/tony/Downloads/ecgpuwave-1.3/principal.f:413: more undefined references to `lnblnk_' follow
collect2: ld returned 1 exit status

Any ideas on how to resolve this issue would be greatly appreciated.

Thank you

---

### Post by gmargo on 2010-03-24
I got it to compile after lifting **lnblnk** source code from here: [http://www-numi.fnal.gov/offline_software/srt_public_context/WebDocs/doxygen/loon/html/hpxgs_2lnblnk_8c-source.html](http://www-numi.fnal.gov/offline_software/srt_public_context/WebDocs/doxygen/loon/html/hpxgs_2lnblnk_8c-source.html).  But now "make check" gives an exception.  (Using fort77 which uses f2c on 9.10 Karmic)

Update: Using g77 on 8.04 Hardy, it compiles (without the lnblnk source) and "make check"s just fine.

---

### Post by taildragger on 2010-03-25
Thank you gmargo! That worked.

I installed 8.04 Hardy and ecgpuwave installed smoothly using g77 and "make check"ed fine too. Thanks again!

I also tried to lift the code you linked but received the original errors shown above when trying to install ecgpuwave on 9.10 Karmic. Maybe I did something wrong: I copied the code from the link into gedit, removed the line numbers, saved as lnblnk.c and placed the file in my working directory /home/tony/Downloads/ecgpuwave-1.3/ Is this correct? 

Thank you again for your time. I really appreciate it!

---

### Post by gmargo on 2010-03-25
The only other change I made to lnblnk.c is to add a #define so the "int lnblnk_(chline, len)" signature was used (with the trailing underscore.)

---

