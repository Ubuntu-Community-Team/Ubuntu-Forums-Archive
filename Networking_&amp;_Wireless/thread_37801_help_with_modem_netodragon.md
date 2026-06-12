---
title: "help with modem netodragon"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by johnnyb on 2005-05-28
I have just installed Ubuntu and it looks and feels great, but I am having a problem installing and configuring my modem. This is my first time using Linux so please take this into consideration.

Under the device manager it says there is a smartlink smartpci561 56k modem, but my modem is a netodragon. There is a driver listed at the netodragon website.

[http://netodragon.com/slmodem-2.9.10_netodragon.tar.gz](http://netodragon.com/slmodem-2.9.10_netodragon.tar.gz)

I am having a problem locating the kernel to make the driver or whatever I have to do.

If you could tell me what I need to put into the makefile I would appreciate it and if you would explain it also that would help me learn.

---

### Post by daxumaming on 2005-07-24
[QUOTE=johnnyb]I have just installed Ubuntu and it looks and feels great, but I am having a problem installing and configuring my modem. This is my first time using Linux so please take this into consideration.

Under the device manager it says there is a smartlink smartpci561 56k modem, but my modem is a netodragon. There is a driver listed at the netodragon website.

[http://netodragon.com/slmodem-2.9.10_netodragon.tar.gz](http://netodragon.com/slmodem-2.9.10_netodragon.tar.gz)

I am having a problem locating the kernel to make the driver or whatever I have to do.

If you could tell me what I need to put into the makefile I would appreciate it and if you would explain it also that would help me learn.[/QUOTE]
 I also have a netodragon 56K with me, but I'll be configuring it after I'm done with my mouse problem. Anyway, I already did some googling and found some solutions that might hopefully help us use the modem with our system. I'm not sure about this but they say we have to download the gcc. Below are the posts:

1. download the *.deb from [http://archive.ubuntulinux.org/ubuntu/pool/main/g/gcc-3.4/](http://archive.ubuntulinux.org/ubuntu/pool/main/g/gcc-3.4/) 

2. Copy all debs, to /var/cache/apt/archives... & issue apt-get install gcc, to actually install 

3. gzip -dc slmdm-2.6.10_netodragon.tar.gz | tar xf - 

I'm not sure if this will work, I will try it once I'm done with my 1st problem. Then I'll post whatever results here. Here are a couple URL's

[http://www.linux-plus.com/phpBB2/viewtopic.php?p=754&](http://www.linux-plus.com/phpBB2/viewtopic.php?p=754&)
[http://www.linux-egypt.org/showthread.php?t=8730](http://www.linux-egypt.org/showthread.php?t=8730)
[http://www.linux-egypt.org/archive/index.php/t-8730.html](http://www.linux-egypt.org/archive/index.php/t-8730.html)

---

