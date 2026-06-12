---
title: "Flash"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by JKobyP on 2010-05-09
I have Ubuntu Restricted Extras downloaded yet flash doesn't seem to work in chrome nor firefox.  I'm using 10.04 and i installed it with wubi.

---

### Post by cogier on 2010-05-09
Try going to the Flash site [http://www.adobe.com/products/flashplayer/]("http://www.adobe.com/products/flashplayer/") and follow the instructions to download.

---

### Post by ddecator on 2010-05-10
Could you be a little more specific as to how it doesn't work? For example, does it not load videos at all? Are you unable to click on Flash elements like the play button on videos?

---

### Post by JKobyP on 2010-05-10
they simply do not load.  I'm not sure whether to choose flash for tar.gz or deb or APT or rpm.

---

### Post by oleink on 2010-05-10
> **JKobyP said:**
> they simply do not load.  I'm not sure whether to choose flash for tar.gz or deb or APT or rpm.

It'd be better if you got flash plugin via the software center.  Then it specifically works on firefox and google chrome should export a copy of the plugin to itself

---

### Post by v1ad on 2010-05-10
i agree with oleink but if u still want to download from the website get either the apt or deb will make it a lot easier on you.

---

### Post by oleink on 2010-05-10
> **v1ad said:**
> i agree with oleink but if u still want to download from the website get either the apt or deb will make it a lot easier on you.

yeah. and deb may be the easiest.  Thanks i forgot to suggest that

---

### Post by JKobyP on 2010-05-10
dpkg: error processing flash.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 flash.deb

This is the message i recieved when i tried to 'sudo dpkg -i' the file using command line

The software manager won't let me install it on account of packages from unauthenticated sources

---

### Post by Kafubie on 2010-05-10
For me, I went to Ubuntu Software Center and uninstall'd flash, then install'd it again.

---

### Post by sandyd on 2010-05-10
see sig.

press remove. (just to make sure)
then press install (x64)

Your using 64-bit ubuntu btw.

---

### Post by oleink on 2010-05-12
> **JKobyP said:**
> dpkg: error processing flash.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 flash.deb

This is the message i recieved when i tried to 'sudo dpkg -i' the file using command line

The software manager won't let me install it on account of packages from unauthenticated sources

You'll need the 64 bit package.  You were trying the 32 bit

---

### Post by fowl on 2010-05-12
Thank you for the easy to use install. It worked without any issues. The only question i have is full screen flash videos still seem to stutter. Any ideas on that?

---

### Post by QIII on 2010-05-12
The poor performance in full screen may be a combination of two things.  One of them  you may be able to address, one you can't.

What you may be able to do is disable compiz temporarily if you use compiz (install compiz-fusion icon and you can toggle between compiz and metacity.)

The second you will not be able to do much about:  Flash is terribly written for Linux.  That's on Adobe, not Linux.  They just haven't taken the time to get in right for Linux.  It is a resource hog of Biblical proportions and runs poorly besides.  Some sites, like Hulu, will just tell you you are out of luck if you are using the 64 bit Linux version of Flash and will show you to the door.

If your machine is multi-core and has a substantial amount of memory, this condition my be mitigated somewhat.

Hulu will still tell you to bugger off.

---

### Post by sir_nasty on 2010-05-12
Most people know that flash is a resource hog. However, the other day I was able to prove/confirm it for myself.  I opened up a video on youtube. Then opened a second tab, searched youtube html 5, and opted in to the html 5 beta.  Open up the cpu manager.  find the same video (now it should be using html 5) play the flash one and watch the meter, stop it, play the html 5 one.... for me it was about 30-50% difference in processor usage in favor of the html 5 version.... I was amazed...

---

### Post by xavierp94 on 2010-05-12
> **Kafubie said:**
> For me, I went to Ubuntu Software Center and uninstall'd flash, then install'd it again.
I'd suggest that too. This worked for me once when I had this problem.

---

### Post by oleink on 2010-05-15
> **fowl said:**
> Thank you for the easy to use install. It worked without any issues. The only question i have is full screen flash videos still seem to stutter. Any ideas on that?

glad it worked besides full screen.. That's is an interesting problem to have all things considered that programming for full screen and regular are pretty much the same

---

