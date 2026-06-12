---
title: "No GUI boot"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Stan% on 2009-01-21
Running Hardy

When I boot, the ubuntu progress bar completes its run, then the screen goes black for about 10 secs., then it shows a number of entries such as....... (white characters on black screen)

b7f96000-b7f97000 r-xp 00000000 07:00 89721      /rofs/usr/lib/xorg/modules/fonts/libfreetype.so

The last such entry is....... 
        bfa7e000-bfa93000 rw-p bffeb000 00:00 0 [stack]

If I ctrl alt F1 it askes for login info and goes into command line mode.
If I ctrl alt F7 nothing happends at all.

The computer is dual booted with Win98 and Win 98 starts fine.

Anyone know anything about this?

---

### Post by handydan918 on 2009-01-21
How about some machine specs? it sounds like an oldie. You may not have the horsepower to run Ubu, or you may not be able to use the livecd. You might need to try the alternate install cd, instead.

---

### Post by Stan% on 2009-01-21
> **handydan918 said:**
> How about some machine specs? it sounds like an oldie. You may not have the horsepower to run Ubu, or you may not be able to use the livecd. You might need to try the alternate install cd, instead.

Yes, it's an oldie. PIII, 500 mghz. I installed ubuntu about 3 months ago and it has been working fine.

Do you need other specs?

---

### Post by caljohnsmith on 2009-01-21
Stan%, can you please post the output of the following:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by Stan% on 2009-01-21
> **caljohnsmith said:**
> Stan%, can you please post the output of the following:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

Yes, but it will take some time. I'm on two different computers on two different floors.

Might not get this posted tonight.

It's not an important computer; just one I keep around for trying new things.

---

### Post by handydan918 on 2009-01-22
> **Stan% said:**
> Yes, it's an oldie. PIII, 500 mghz. I installed ubuntu about 3 months ago and it has been working fine.

Do you need other specs?
A p3 is good enough...how much ram?

---

### Post by Stan% on 2009-01-22
> **handydan918 said:**
> A p3 is good enough...how much ram?

256 mb; it will max out at 384mb

---

### Post by Stan% on 2009-01-23
> **caljohnsmith said:**
> Stan%, can you please post the output of the following:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

sudo fdisk -lu

disk  /dev/sda1  20.5 GB 20547841536 bytes
255 heads, 63 sectors/track, 2498 cyl., total 40123503 sectors
units= sectors of 1* 512= 512bytes
disk identifier: 0x0002bbdc
device    boot  start    end       blocks   id  system
sda1      *    63       4096574   2048256  b   win95 fat32
sda3           6056505  25591544  9767520  83  Linux
sda4           25591545 26764289  586372+  82  linux swap/solaris
disk sdb: 4324 mb 4324368384 bytes 255 heads, 63 sectors/track, 525 cyl., total 8446032 sectors
units= sectors of 1 * 512= 512 bytes
disk identification 0x00000001
device  boot  start  end       block    id  system
sdb1    *     16128   4112639   2048256  b   win95 fat32
sdb2          63      16064     8001     1   fat12 
sdb3          4112640 5911919   899640   da  non-fs data
partition tables are not in disk order. 

sudo blkid -c /dev/null

sda1: LABLE "Gateway" uuid= "236e-1609" TYPE= vfat 
sda3: uuid="462b43d2-b3c0-4f21-9195-b6a675eb86ce" TYPE+ ext3
sda4: TYPE= "swap uuid= "de5e6165-8792-4f7b-8d44-ab5bde42d01c"
sdb1: Label "Gateway" uuid="236e-1609" TYPE "vfat"
sdb2: sec_type= "ms-dos" LABEL= "Fat_16" uuid= "1806-1b1a" TYPE="VFAT"


cat /etc/fstab
#/etc/fstab: static file system information
#
#<FILE SYSTEM> <MOUNT POINT> TYPE <OPTIONS> <DUMP> <PASS>
proc            /proc        proc  default   0      0
#/dev/sda3 
uuid= 462b43d2-b3c0-4f21-9195-b6a675ed86ce / ext3 relatime,error s= remount-ro 0 1
#/dev/sda4 uuid= de5e6165-8792-4f7d-8b44-ab5bde42d01c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf, iso9660, user,noauto, exec, utf8 0 0
/dev/fd0 /media/floppy auto, rw, user, noauto, exec, utf8, 0 0

Note: the "relatime, error" is not a miss print; it shows just that way on the monitor.

Note: I may not have understood the followimg command.

cat /etc/initramfs-tools/conf.d/resume/[/CODE][/QUOTE]

resume=uuid= de5e6165-8792-4f7b-8d44-ab5bde42d01c
cat: [/CODE] no such file or dir
cat: [/QUOTE] no such file or dir

End of results of your commands.

---

### Post by caljohnsmith on 2009-01-23
One cause of losing the Ubuntu splash screen on boot is if the swap partition UUID changes for some reason (usually resizing or moving it); but that's obviously not your case, so I don't know off-hand why you lost your splash screen at boot time. As handydan918 has all ready pointed out, your computer is a bit old without much RAM, so that might be the issue even though you've gotten away with it up until now. Did you download any package updates prior to when you started having problems? Or can you give any clues as to what led up to the problem?

---

### Post by Stan% on 2009-01-23
> **caljohnsmith said:**
> One cause of losing the Ubuntu splash screen on boot is if the swap partition UUID changes for some reason (usually resizing or moving it); but that's obviously not your case, so I don't know off-hand why you lost your splash screen at boot time. As handydan918 has all ready pointed out, your computer is a bit old without much RAM, so that might be the issue even though you've gotten away with it up until now. Did you download any package updates prior to when you started having problems? Or can you give any clues as to what led up to the problem?

There were some updates but it ran okay for a few days after those so updtes are not likely the cause.

I tried to run apt-get update from command line but I get a bunch of messages that it can't resolve this and can't resolve that. Do I need to give any other command before apt-get; like mount router or anything else?

---

### Post by caljohnsmith on 2009-01-24
> **Stan% said:**
> There were some updates but it ran okay for a few days after those so updtes are not likely the cause.

I tried to run apt-get update from command line but I get a bunch of messages that it can't resolve this and can't resolve that. Do I need to give any other command before apt-get; like mount router or anything else?
Do you mean "cannot resolve host" type errors? If so, that's usually a networking problem. Do you have a working internet connection within Ubuntu on that computer when you do the "apt-get update"?

---

### Post by Stan% on 2009-01-24
> **caljohnsmith said:**
> Do you mean "cannot resolve host" type errors? If so, that's usually a networking problem. Do you have a working internet connection within Ubuntu on that computer when you do the "apt-get update"?

When I run apt-get update I get a number of entries such as:
 
w: failed to fetch http:security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/translation-en_us.bz2  Could not resolve 'security.ubuntu.com' 

None of them say "cannot resolve host". They all seem to be reguarding repos and archives.

Could the problem be video drivers? How can I reinstall drivers from console mode?

---

### Post by caljohnsmith on 2009-01-24
Sounds to me like you have a networking problem. How about trying:
```
ping -c3 www.google.com
```
If that gives a "cannot resolve host" error, try:
```
ping -c3 74.125.19.104
```
Let me know what those commands return. Also, I don't think you mentioned yet, but do you know if you have internet connectivity while you are in Ubuntu?

---

### Post by Stan% on 2009-01-25
> **caljohnsmith said:**
> Sounds to me like you have a networking problem. How about trying:
```
ping -c3 www.google.com
```
If that gives a "cannot resolve host" error, try:
```
ping -c3 74.125.19.104
```
Let me know what those commands return. Also, I don't think you mentioned yet, but do you know if you have internet connectivity while you are in Ubuntu?

Ping Google = unknown host
Ping 74.125.19.104 = network is unreachable

A broadband/cable connection was working fine before this "no gui boot"

From lspci

00:11.0 ethernet controller: atheros communications inc. ar5212/ar5213 multiprotocol mac/baseband processor (rev01)

also 

01:00.0 vga compatible controller: nvidia corp. nv5m64 [riva tnt2 model 64/model 64 pro] rev 15

---

### Post by caljohnsmith on 2009-01-25
So you don't have internet connectivity any more in Ubuntu, so I'm wondering what else might be wrong with your install. Would saving your important documents from your Ubuntu partition, and then reinstalling Ubuntu be an option you could consider? Or is your Ubuntu heavily customized?

---

### Post by Stan% on 2009-01-25
> **caljohnsmith said:**
> So you don't have internet connectivity any more in Ubuntu, so I'm wondering what else might be wrong with your install. Would saving your important documents from your Ubuntu partition, and then reinstalling Ubuntu be an option you could consider? Or is your Ubuntu heavily customized?

Reinstalling is no problem at all. I may continue for a while to try and find a fix; just because I'm couriuos. I feel that if I can get the GUI back I can correct anything else too.

BTW I've tried different kernels and recovery mode but nothing yet has gotten GUI back.

Thanks for your help. If you think of anything else I'll be checking back on this thread and you may email me.

---

### Post by Stan% on 2009-02-06
> **Stan% said:**
> Reinstalling is no problem at all. I may continue for a while to try and find a fix; just because I'm couriuos. I feel that if I can get the GUI back I can correct anything else too.

BTW I've tried different kernels and recovery mode but nothing yet has gotten GUI back.

Thanks for your help. If you think of anything else I'll be checking back on this thread and you may email me.

Update:

I wiped the entire hard drive, reinstalled Win98, popped in the Hardy live cd but it wouldn't install. Tried several times.

Dled and burned a new Hardy, still wouldn't install.

I tried an old 7.04; what was that, Gusty?, it started to install but I didn't want Gusty so I stopped it.

I dled and burned Ibex and it installed fine, albeit a little slow. 

I'll continue using Ibex and mark this thread closed. 

Thanks for all the help.

---

### Post by Stan% on 2009-02-06
> **Stan% said:**
> Update:

I wiped the entire hard drive, reinstalled Win98, popped in the Hardy live cd but it wouldn't install. Tried several times.

Dled and burned a new Hardy, still wouldn't install.

I tried an old 7.04; what was that, Gusty?, it started to install but I didn't want Gusty so I stopped it.

I dled and burned Ibex and it installed fine, albeit a little slow. 

I'll continue using Ibex and mark this thread closed. 

Thanks for all the help.

Okay, guess I can't mark it solved right now.

---

