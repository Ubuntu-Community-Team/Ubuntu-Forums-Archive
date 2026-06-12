---
title: "Flash Install - Wrong Architecture i386"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by parsimony on 2009-04-10
I am trying to install Flash

but I get the error - Wrong Architecture i386

:confused:

---

### Post by llamabr on 2009-04-10
How are you trying to install it?  And what type of system do you have?

---

### Post by parsimony on 2009-04-10
Thanks

using Firefox - the .deb version - with package installer

Ubuntu 8.10 wubi installed today

My system is a Dell 1545 C2D

---

### Post by lisati on 2009-04-10
> **parsimony said:**
> Thanks

using Firefox - the .deb version - with package installer

Ubuntu 8.10 wubi installed today

My system is a Dell 1545 C2D
You're not using a 64-bit system by any chance?

---

### Post by parsimony on 2009-04-10
How do I know if its 64 bit - its a Core 2Duo - and its Windows 7

Thanks

uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux

If I am using the 64-bit version that's weird - I didn't chose it - just wubi installed it - how can I get wubi to install the 32 bit version?

Now wiping my 64-bit version which wubi installed by default and manually downloading 32-bit iso and re-running wubi.

---

### Post by ivanvajar on 2009-04-10
To install codecs, flash and everything else in 32-Bit Ubuntu:

> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

---

### Post by oldos2er on 2009-04-10
"If I am using the 64-bit version that's weird - I didn't chose it - just wubi installed it - how can I get wubi to install the 32 bit version?"

 Wubi checks if you have a 64-bit capable processor; if you do, it installs 64-bit Ubuntu.

---

### Post by sandyd on 2009-04-10
i guess he has to install 64 bit flash

hread this 


[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by parsimony on 2009-04-11
SOLUTION

This was to force install by Wubi of 32-bit version

You do this by downloading the 32-bit iso into the same directory that wubi.exe resides in - then wubi will intsall that version rather than the default 64-bit - this then makes installing apps (most which are still 32-bit) much easier.

:p

---

### Post by Paqman on 2009-04-11
> **carlee said:**
> i guess he has to install 64 bit flash

hread this 


[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

You can use 32-bit Flash on 64-bit Ubuntu no problems. Just install the normal flashplugin-nonfree, the system will take care of all the rest for you.

---

### Post by oldos2er on 2009-04-11
> **parsimony said:**
> 
You do this by downloading the 32-bit iso into the same directory that wubi.exe resides in - then wubi will intsall that version rather than the default 64-bit - this then makes installing apps (most which are still 32-bit) much easier.
:p

 We've had both 64-bit Flash and Java available for awhile now, as well as all the apps in the 64-bit repositories, the installation of which is the same as for 32-bit programs.

 Why didn't you install 64-bit Flash?

---

