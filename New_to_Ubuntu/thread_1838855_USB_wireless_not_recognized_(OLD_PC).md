---
title: "USB wireless not recognized (OLD PC)"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by maazrizki on 2011-09-04
I am trying convert myself from Windows world to Linux world (i.e. Ubuntu).
I have a old pc bios 1999 (micronpc), pentium 3, ram 220MB, speed 600MHZ.
8.10 ubuntu got installed. Any higher version gives Black screen. Anyway, 8.10 shows Wireless net work tab in network configuration but USB wireless do not get activated. somewhere on internet somebody suggested to copy .inf, .sys, .dll files from windows for usb wireless to ubuntu. I tried but I could not find .inf on my laptop, I found .sys, .dll, I put them on usb memory stick and try to copy them. I don't know where to copy via ubuntu file manager. Anyway I tried but files are locked on usb stick.
On the other hand when I put live Koppix cd that recognize wireless.
Please help before I revert back to windows world already wasted 2 weeks.
Desperate 
MR :(

---

### Post by sanderd17 on 2011-09-04
Sorry, but 8.10 isn't supported anymore.

That means you will not be able to install new softare or upgrade software.

For your system, I would try Lubuntu: [http://lubuntu.net/](http://lubuntu.net/)

Newer versions come with other drivers, so you won't probably have the same problem. If you still have the same problem, give us the output of the command

```

lsusb

```

BTW, you shouldn't have waisted 2 weeks before you came here. The strong part of Ubuntu is the community.

---

### Post by philipballew on 2011-09-04
For help with the blank screen if lubuntu does that I can help here. Install lubuntu and tell me if you get an error or not

---

### Post by maazrizki on 2011-09-05
I used lubuntu it gives me following screen as attached. 
For second reply, I get blank screen with ubunto 10.10, lxde , pclinux
However, now the good news is I tried LinuxMint live cd in compatiable mode it loads it sees my usb wifi stick. 
What you guys suggest shall I go with it or give Lubuntu another chance? Personally I like ubunto flavor more than others.
 
Still confused :confused:
 
MR

---

### Post by sanderd17 on 2011-09-05
It's simply not possible to run Mint live with only 220MB RAM. Are you sure those are your specs?

---

### Post by philipballew on 2011-09-05
install lubuntu is my recommendation. We hare can have it running great :)
also: what kind of wifi stick is it? run "lsusb" like the other person said and that will say what is up with your wifi

---

### Post by maazrizki on 2011-09-05
lsusb from Mint Linux live CD is
Bus 004 Device 001: ID ld6b:0001 Linux Fundation 1.1 root hub
Bus 003 Device 001: ID ld6b:0001 Linux Fundation 1.1 root hub
Bus 002 Device 001: ID ld6b:0001 Linux Fundation 1.1 root hub
Bus 001 Device 003: ID ID 0718:060b Imation Corp.
Bus 001 Device 002: ID 160a:3184 VIA Technologies, Inc. VIA VNT - 6656 [WiFi 802.11b/g USB Dongle]
Bus 001 Device 001: ID ld6b:0002 Linux Fundation 2.0 root hub
 
By the way I had not connected any UTP i.e. Lan wire to my pc I am just trying Wireless to work
 
Plus I would love to install Lubuntu if move any further then four dots on (. . . ) install cd.
 
 
 
MR

---

### Post by philipballew on 2011-09-05
You should download a new iso of lubuntu and see if you perhaps have a bad iso before you go into troubleshooting the install of lubuntu

---

### Post by maazrizki on 2011-09-05
BTW I have Linux Mint 11 Katya, my spec. are same as I wrote before

---

### Post by maazrizki on 2011-09-05
I have three ISO. I checked md5 key all match. however when I use same CD on some other laptop everything works fine till end. At end I get blank screen. But this PC just refuse to go anything further then 4 dots. Or get problem as I shown in one of previous post.
 
Plus thank-you all for quick replies,
 
MR

---

### Post by anewguy on 2011-09-06
If Mint is anything like Ubuntu, you will probably need to download the alternate CD to install in that kind of memory.  It uses "terminal" graphics instead of a more resource heavy GUI'd environment.

Dave ;)

---

### Post by philipballew on 2011-09-06
How about you download lubuntu alternative and then install that. then we can diagnose any xorg or whatever errors from there?
this might be a good way and you can see how this works? [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by maazrizki on 2011-09-06
I'll try alternate CD's
 
Now we are talking
 
Thanks,
MR

---

### Post by philipballew on 2011-09-06
Okay, This is going to install a command line environment only, however you will install the desktop on top. if it boots into the cli after you install it you can assume its something related to the x  graphics server?

---

### Post by wildmanne39 on 2011-09-07
Hi, I just wanted to let you know that I did some research and the driver for your usb wireless is included in 11.04, I know you can not use 11.04 but if it is in ubuntu 11.04 then it is probably in Lubuntu 11.04.
Thank you

---

### Post by philipballew on 2011-09-07
All drivers are gonna be in Lubuntu that are in Ubuntu because they both ship with the stock 2.6.38 Linux kernel. The only difference between Lubuntu and Ubuntu is Lubuntu uses LXDE as a desktop interface and Ubuntu uses Gnome.
[https://secure.wikimedia.org/wikipedia/en/wiki/LXDE]("https://secure.wikimedia.org/wikipedia/en/wiki/LXDE") 

[https://secure.wikimedia.org/wikipedia/en/wiki/GNOME]("https://secure.wikimedia.org/wikipedia/en/wiki/GNOME")

---

### Post by wildmanne39 on 2011-09-07
Hi philipballew, that is what I thought also but I did not want to state that since I could not confirm it.
Thank you

---

### Post by maazrizki on 2011-09-07
Well I gave up, even minimal did behave as expected. Anyway, I had xubuntu 10.10 CD with me. I tried that, it worked. I installed it, then today pc start doing some kind of updates, after few file installations, it start saying it will take 3 hours plus to install some updates. Mouse stop working, PC froze. One thing, this time I did different was I connected lan wire to PC.
I gave up now because this PC is only good for Window 2000. 
Soon I will start new threads for old lap tops, let see how much sucsessfull I am there.
 
Lost war
 
:lolflag:
 
MR

---

### Post by wildmanne39 on 2011-09-07
Hi, I am sorry to hear that good luck with future computers and ubuntu.

---

