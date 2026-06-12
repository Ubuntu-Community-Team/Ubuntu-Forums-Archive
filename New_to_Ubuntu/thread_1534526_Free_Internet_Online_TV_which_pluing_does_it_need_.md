---
title: "Free Internet Online TV: which pluing does it need or apt-get ?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-07-19
Hi

[http://www.freetvonline.com/Visitors.php?Sections](http://www.freetvonline.com/Visitors.php?Sections)[Primary]=Live_TV&Actions[Primary]=Overview#

I get a frame with PLUGING to be installed. Which one? It works under Windows XP but not under LINUX :( :-( :-(

Best regards

---

### Post by SkyNet2029 on 2010-07-19
Hi. You need to install the gstreamer0.10-ffmpeg package.

```
$ sudo apt-get install gstreamer0.10-ffmpeg
```

That is how I got it to work here. I use Ubuntu 10.04 64bit.

Hope that helps. 
Cool site btw.

---

### Post by sunshine316 on 2010-07-20
just installed the plugin and it didnt work for me :/

---

### Post by noidian on 2010-07-20
try installing the vlc player. It will normally install the other weird codecs required. Most of my online tv works except for specific ones which have their own software.e.g. veetle
Browser:
Also, try firefox browser instead of the other ones.This works most of the time for me.

---

### Post by frenchn00b on 2010-07-21
> **SkyNet2029 said:**
> Hi. You need to install the gstreamer0.10-ffmpeg package.

```
$ sudo apt-get install gstreamer0.10-ffmpeg
```

That is how I got it to work here. I use Ubuntu 10.04 64bit.

Hope that helps. 
Cool site btw.


1)
```

a# apt-get install  gstreamer0.10-ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libavformat52 libpostproc51 libswscale0
The following NEW packages will be installed:
  gstreamer0.10-ffmpeg libavformat52 libpostproc51 libswscale0
0 upgraded, 4 newly installed, 0 to remove and 59 not upgraded.
Need to get 1,132kB of archives.
After this operation, 2,916kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libavformat52 libpostproc51 libswscale0
Install these packages without verification [y/N]? y
Get:1 http://ftp.at.debian.org squeeze/main gstreamer0.10-ffmpeg 0.10.10-1 [161kB]
Get:2 http://www.debian-multimedia.org squeeze/main libavformat52 5:0.6~svn20100603-0.0 [793kB]
Get:3 http://www.debian-multimedia.org squeeze/main libpostproc51 5:0.6~svn20100603-0.0 [40.8kB]
Get:4 http://www.debian-multimedia.org squeeze/main libswscale0 5:0.6~svn20100603-0.0 [138kB]
Fetched 1,132kB in 3s (354kB/s)    
Selecting previously deselected package libavformat52.
(Reading database ... 75768 files and directories currently installed.)
Unpacking libavformat52 (from .../libavformat52_5%3a0.6~svn20100603-0.0_i386.deb) ...
Selecting previously deselected package libpostproc51.
Unpacking libpostproc51 (from .../libpostproc51_5%3a0.6~svn20100603-0.0_i386.deb) ...
Selecting previously deselected package libswscale0.
Unpacking libswscale0 (from .../libswscale0_5%3a0.6~svn20100603-0.0_i386.deb) ...
Selecting previously deselected package gstreamer0.10-ffmpeg.
Unpacking gstreamer0.10-ffmpeg (from .../gstreamer0.10-ffmpeg_0.10.10-1_i386.deb) ...

Setting up libavformat52 (5:0.6~svn20100603-0.0) ...
Setting up libpostproc51 (5:0.6~svn20100603-0.0) ...
Setting up libswscale0 (5:0.6~svn20100603-0.0) ...
Setting up gstreamer0.10-ffmpeg (0.10.10-1) ...


```

I quit firefox and restart it

unfortutnaly I get :
[http://img688.imageshack.us/img688/7716/shot2e.jpg](http://img688.imageshack.us/img688/7716/shot2e.jpg)

---

### Post by Keith_K on 2010-07-21
I had to uninstall totem to get another player to work

---

### Post by SkyNet2029 on 2010-07-21
Hmmm...
The only KEY difference I see here is that your repos point to the debian-multimedia repositories. 
I use the standard ubuntu ones.
Perhaps there is a different package than the standard ubuntu one being installed?

---

