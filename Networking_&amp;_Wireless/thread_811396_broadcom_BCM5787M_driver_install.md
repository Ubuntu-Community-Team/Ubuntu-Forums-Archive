---
title: "broadcom BCM5787M driver install"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by igordeq on 2008-05-29
Hello, trying to make the wifi work on Hardy but no luck.

I have an Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express 5787(rev 02). After entering Broadcom i found a driver for 5787 (linux-3.85l.zip) which has both a .rpm and tar.gz files.For some reason , this time, i cant untar nor open de .rpm files.I have done it in the past and not sure where the errror is this time. Can anyone help?

grazie mille

---

### Post by MaindotC on 2008-05-29
Uncompress the .tar.gz file by typing:
[code]
tar xvf linux-3.85l.tar.gz
[code]
This will extract the files into a folder with the same name but it won't have the .tar.gz extension.  Navigate into the folder and there should be a README file.  That should tell you how to install the driver.  If not, tell me what's there and we can guide you from there.

---

### Post by MaindotC on 2008-05-29
Actually I found the file you downloaded and these are the directions in the README file that are separate from the .tar.gz's:
[code]
Building Driver From TAR File
=============================

The following are general guidelines for installing the driver.

1. Create a directory and extract the files:

   tar xvzf tg3-<version>.tar.gz

2. Build the driver tg3.o (or tg3.ko) as a loadable module for the
running kernel:

   cd src
   make

The driver will be compiled for the running kernel by default. To build
the driver for a kernel different than the running one, specify the
kernel by defining it in KVER:
[code]
and they go on to explain how to build and install this driver.

---

### Post by igordeq on 2008-05-29
Thanks Allan, I am a very beginner user and cant do any of it properly yet.I feel going in circles. I´ll break down my actions:

1. from terminal I go to my desktop (cd Desktop) where my driver (linux-3.85l.zip). There I take out tg3-3.85l.tar.gz and place on desktop

2. But then it wont let me untar: not even with sudo
[I]
tar: linux: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now[/I]

Also:
Trying to follow the guide lines ...

1. Create a directory and extract the files:

tar xvzf tg3-<version>.tar.gz

2. Build the driver tg3.o (or tg3.ko) as a loadable module for the
running kernel:

cd src
make

 ..... I fail.:confused:

 and grazie!



Just in case: i have a BAREBONE FT00 IC2DUO NVIDIA 8400 GS 256MB Intel Core 2 Duo  (Merom) y (Penryn), 800MHz FSB, Socket P  
- Chipset: Intel Crestline PM965 + ICH8-M

---

### Post by MaindotC on 2008-05-29
Enter this command:
```

tar xvzf tg3_sup-3.85l.tar.gz

```
or this command:
```

tar xvzf tg3-3.851.tar.gz

```
If you can't do that, make sure you have the program called "tar" which I can't believe you wouldn't have.

---

### Post by MaindotC on 2008-05-29
igordeq I'm going to bed so if you need more help I hope you can find someone else read you the directions in the readme file.  I'll be back on in like 12 hours.

---

### Post by igordeq on 2008-05-29
I follow the command:
[I]
igor@igor-laptop:~/Desktop$ tar xvzf tg3-3.85l.tar.gz
tg3-3.85l/
tg3-3.85l/tg3.4
tg3-3.85l/tg3.c
tg3-3.85l/tg3.h
tg3-3.85l/ChangeLog
tg3-3.85l/LICENSE
tg3-3.85l/README.TXT
tg3-3.85l/Makefile
tar: tg3-3.85l: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors[/I]

I´ll keep searching and good night

---

### Post by MaindotC on 2008-05-29
I don't know what the utime business is but you have all the files you need extracted.  Use the "cd" command to move into the directory that was just created - it should be:
```

cd tg3-3.851/

```
Then type:
```

make

```

---

### Post by igordeq on 2008-05-29
Yes, i did as follows:

igor@igor-laptop:~$ cd Desktop/tg3-3.85l
igor@igor-laptop:~/Desktop/tg3-3.85l$ make
make -C /lib/modules/2.6.24-17-generic/build SUBDIRS=/home/igor/Desktop/tg3-3.85l modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/igor/Desktop/tg3-3.85l/tg3.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/igor/Desktop/tg3-3.85l/tg3.mod.o
  LD [M]  /home/igor/Desktop/tg3-3.85l/tg3.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'

After i made *make install*:

igor@igor-laptop:~/Desktop/tg3-3.85l$ sudo make install
[sudo] password for igor: 
make -C /lib/modules/2.6.24-17-generic/build SUBDIRS=/home/igor/Desktop/tg3-3.85l modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
mkdir -p /lib/modules/2.6.24-17-generic/kernel/drivers/net;
install -m 444 tg3.ko /lib/modules/2.6.24-17-generic/kernel/drivers/net;
install -m 444 tg3.4.gz /usr/share/man/man4;\

---

### Post by MaindotC on 2008-05-29
Generally you thank people who take the time to read you directions that are in the README file sitting on your computer.

---

### Post by igordeq on 2008-05-29
Sorry Allan I thought we hadnt finish the operation and that why my telegraphic manner! Im more than thankful for you help, have no doubt.
In fact there are no signs of the wifi yet...

sleep well

---

### Post by MaindotC on 2008-05-29
Will someone please help this kid complete the installation - I'm pasting the directions so you can tell him what an insmod is and so forth.  I'm going to bed.

---

### Post by MaindotC on 2008-05-29
bump - just woke up

---

