---
title: "Ndiswrapper,AMD64 &amp; 2Go of RAM"
date: 2005-04-28
forum: Networking &amp; Wireless
---

### Post by mat2057 on 2005-04-28
Hello
I have installed Hoary, ndiswrapper, wpa_supplicant and everything was ok.
Yesterday I bought 1 Go of RAM so I have 2Go...  But during the boot, when it starts ndiswrapper, it freezes... I install everyting again, but when I add drivers for ndiwrapper, I get a strange message... (WMP54GS : Broadcom for Windows x64). I enter "modprobe ndiswrapper" and it freezes. I reboot, try to load it again and another freeze. Here is what I got :
ndiswrapper installation:
```
:~/ndiswrapper-1.1$ make
make -C driver
make[1]: entrant dans le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/driver Â»
make -C /lib/modules/2.6.10-5-amd64-generic/build SUBDIRS=/home/matt/ndiswrapper-1.1/driver \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[2]: entrant dans le rÃ©pertoire Â« /usr/src/linux-headers-2.6.10-5-amd64-generic Â»  CC [M]  /home/matt/ndiswrapper-1.1/driver/hal.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/iw_ndis.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/loader.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/misc_funcs.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/ndis.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/ntoskernel.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/pe_linker.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/proc.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/wrapper.o
  CC [M]  /home/matt/ndiswrapper-1.1/driver/usb.o
  AS [M]  /home/matt/ndiswrapper-1.1/driver/x86_64_stubs.o
  LD [M]  /home/matt/ndiswrapper-1.1/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/matt/ndiswrapper-1.1/driver/ndiswrapper.mod.o
  LD [M]  /home/matt/ndiswrapper-1.1/driver/ndiswrapper.ko
make[2]: quittant le rÃ©pertoire Â« /usr/src/linux-headers-2.6.10-5-amd64-generic Â»
make[1]: quittant le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/driver Â»
make -C utils
make[1]: entrant dans le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/utils Â»
cc -Wall -g -DNDISWRAPPER_VERSION=\"1.1\"    -c -o loadndisdriver.o loadndisdriver.c
gcc -o loadndisdriver loadndisdriver.o
make[1]: quittant le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/utils Â»

:~/ndiswrapper-1.1$ sudo make install
make -C driver install
make[1]: entrant dans le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/driver Â»
make -C /lib/modules/2.6.10-5-amd64-generic/build SUBDIRS=/home/matt/ndiswrapper-1.1/ driver \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[2]: entrant dans le rÃ©pertoire Â« /usr/src/linux-headers-2.6.10-5-amd64-generic Â»
  Building modules, stage 2.
  MODPOST
make[2]: quittant le rÃ©pertoire Â« /usr/src/linux-headers-2.6.10-5-amd64-generic Â»
mkdir -p /lib/modules/2.6.10-5-amd64-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.10-5-amd64-generic/misc
/sbin/depmod -a
make[1]: quittant le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/driver Â»
make -C utils install
make[1]: entrant dans le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/utils Â»
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

make[1]: quittant le rÃ©pertoire Â« /home/matt/ndiswrapper-1.1/utils Â»
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
```

installation of driver:
```
~$ sudo ndiswrapper -i BCMWL564.INF
Installing bcmwl564
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
```

if no driver is installed :
```
~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-amd64-generic/misc/ndi swrapper.ko): Operation not permitted
```
I haven't changed anything in my pc, and I tested my ram with memtest : no error
Thanks to all and I apologize for my English... :rolleyes:
Matt

---

### Post by arbearce on 2005-04-28
when you do a ndiswrapper -l does it show that both driver and hardware are present?

I have also heard that there might be a problem with broadcom card/drivers and over 1gb of ram, not sure if that is what is causing your problems or not.

---

### Post by mat2057 on 2005-04-28
When I do "ndiswrapper -l" I get "hardware present".
I've just removed 1Go of RAM and I managed to load ndiswrapper. I put the RAM again, and freeze. I ran Memtest and no problem...
:'(

Is there a command to load a program in a part of memory ?
Matt

---

### Post by arbearce on 2005-04-28
You could try and add this to you kernel line for boot.

mem=512

[https://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=118165#c18](https://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=118165#c18)

[https://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=118165#c22](https://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=118165#c22)

do this to see where it stops booting at .. not really a solution though.

---

### Post by mat2057 on 2005-04-29
I will add "mem=1024" instead. But will will the next 1024Mo of RAM be used if I do this ?
I ran memtest again : no problem, that's crazy :'(
Thanks, I'm going to try.
Matt

---

### Post by sjansen on 2005-04-29
[QUOTE=mat2057]I will add "mem=1024" instead. But will will the next 1024Mo of RAM be used if I do this ?[/QUOTE]

It will not. You are telling the kernel to ignore the extra gig of RAM. Report the problem to the ndiswrapper developers and hope it isn't a limitation of the proprietary driver you're using.

---

### Post by mat2057 on 2005-04-29
OK I will do report it.
The command line is "uppermem=1048576" ? because "mem=1024" doesn't exists... ?
Matt

---

### Post by mat2057 on 2005-04-29
"uppermem 1048576" doesn"t work. Grub limits the memory, but when I do "cat /proc/meminfo" if get 2048 Mo of RAM, so it freezes..
But mem=1024M works.
I saw it doesn't freeze, but the CPU load is 100% and it doesn't react... but I managed to do "modprobe -r ndiswrapper" (in 5 minutes...) and I was able to work again...
I posted it on ndiswrapper forum.
Matt

---

