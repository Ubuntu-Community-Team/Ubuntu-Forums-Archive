---
title: "Banshee won't play music"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-08
Hey everyone, 

Whenever I try to play my music, I have to use Rhythmbox, because when I use Banshee (my favourite player), I get this message:

```
[Info  14:03:59.004] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, x86_64) @ 2009-10-19 15:42:39 UTC]
[Info  14:04:02.642] All services are started 2.960279s
[Info  14:04:06.694] nereid Client Started
[Error 14:04:14.668] GStreamer resource error: NotFound

``` 

GStreamer resource error: NotFound

This is strange, because RB does playback just fine. Any suggestions?

---

### Post by asuastrophysics on 2009-11-08
no one knows????

I've got ubuntu-restricted extras already installed, can't seem to figure out why one mp3 player would work and not others. :confused:

---

### Post by asuastrophysics on 2009-11-22
BUMP!

I have looked at other threads w/ the same issue, none have remedied my problem. 

I have tried playing HDD-stored mp3's in Banshee on 3 identical ubuntu karmic machines. Every single one shows the same error. I'm going to email the Ubuntu repository team. Banshee needs to be removed from the repo. It simply doesn't work with udev. Therefore, it won't work with any new version of Ubuntu. Unless the bug is fixed, Banshee is garbage obsolete, and depreciated. (and any other word you can think of for useless code)

---

### Post by gackt on 2009-11-22
Hi there, 

This might Help

[http://forum.foresightlinux.org/index.php?topic=445.0](http://forum.foresightlinux.org/index.php?topic=445.0)

Cheers,

---

### Post by vgrisham on 2009-12-08
I had this problem right after a fresh install of Karmic. I did two things and the problem went away.

1. I ran 'sudo apt-get build-dep banshee' from the terminal and installed a bunch of dependencies.
2. I then installed gstreamer-plugins- (good, bad and ugly)

After restarting Banshee, it played fine.

---

### Post by asuastrophysics on 2009-12-08
> **vgrisham said:**
> I had this problem right after a fresh install of Karmic. I did two things and the problem went away.

1. I ran 'sudo apt-get build-dep banshee' from the terminal and installed a bunch of dependencies.
2. I then installed gstreamer-plugins- (good, bad and ugly)

After restarting Banshee, it played fine.

```
jake@jake-laptop:~$ sudo apt-get build-dep banshee
[sudo] password for jake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autoconf automake autotools-dev boo cli-common-dev diffstat intltool
  libclutter-1.0-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev
  libipod-cil libipodui-cil libkarma-cil libkarma0 libmono-cecil-private-cil
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-dev
  libmono-getoptions2.0-cil libmono-i18n-west1.0-cil libmono-management2.0-cil
  libmono-peapi2.0-cil libmono-relaxng1.0-cil libmono-security1.0-cil
  libmono-sharpzip0.84-cil libmono-system-data1.0-cil
  libmono-system-runtime1.0-cil libmono-system-web1.0-cil
  libmono-system1.0-cil libmono0 libmtp-dev libsqlite3-dev libtagc0 libusb-dev
  libxml-dom-perl libxml-perl libxml-regexp-perl libxml2-dev libxxf86vm-dev
  mono-2.0-devel mono-csharp-shell mono-devel mono-gmcs mono-utils
  monodoc-base quilt x11proto-xf86vidmode-dev
0 upgraded, 47 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.2MB of archives.
After this operation, 46.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

**Wow!** :D
That definitely explained quite a bit. Thanks! I'm going to check the gstreamer plugins here in a bit. I'm just surprised all these dependencies weren't installed by default. ;)

---

### Post by mason240 on 2011-02-17
> **vgrisham said:**
> I had this problem right after a fresh install of Karmic. I did two things and the problem went away.

1. I ran 'sudo apt-get build-dep banshee' from the terminal and installed a bunch of dependencies.
2. I then installed gstreamer-plugins- (good, bad and ugly)

After restarting Banshee, it played fine.

I did step one it worked for me! Thank you! 


Notes for others:
I had a clean install of Ubuntu 10.04
Looking through the list of installed stuff, it appears that the gstreamer plugins come with 10.04

---

### Post by yello_downunder on 2011-05-18
Step 1. above fixed banshee for me.  Running 11.04 (Natty)

---

