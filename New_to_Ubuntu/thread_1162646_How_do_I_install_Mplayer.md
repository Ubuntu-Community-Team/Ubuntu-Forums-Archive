---
title: "How do I install Mplayer?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by gshockxc on 2009-05-17
I'm trying to install Mplayer so that I can listen to streaming audio, video, etc.  I found the instructions, but I'm still completely noob, so I don't know all the steps to unpacking .tar.gz files, and such.  I'm using Jaunty and running Firefox 9.04.  Thanks.

Sorry, forgot to include the details..
[http://www.linux-sxs.org/multimedia/mplayermozplug.html](http://www.linux-sxs.org/multimedia/mplayermozplug.html)
[http://www.linux-sxs.org/multimedia/mplayer.html](http://www.linux-sxs.org/multimedia/mplayer.html)

---

### Post by pspsampsp on 2009-05-17
oh sorry didnt see you were using kubuntu in that case go into a terminal and do the command "sudo apt-get install mozilla-mplayer"

---

### Post by mc4man on 2009-05-17
Try here instead
Note that the gui mplayer (gmplayer will not be installed, use smplayer instead
(or just install smplayer and the mplayer build available from it's ppa

[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

smplayer info
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)



Edit:
> but I'm still completely noob
(just in case

To install the smplayer ppa

System -> Administration -> Software Sources -> Third pary -> add 

**Also didn't see kubuntu, use kubuntu's method to add third party sources**

Possibly K menu -> System menu -> Adept Manager -> Sources -> Edit Software Sources -> Third party ...

Copy this line and paste into box -> click add source

```
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu jaunty main
```

Then repeat for this line

```
deb-src http://ppa.launchpad.net/rvm/mplayer/ubuntu jaunty main
```

Then click close and reload (ignore warning

Then this will install a recent mplayer and smplayer
```

sudo apt-get install mplayer smplayer
```

(You'll get warning about unauthenicated blah, blah, ignore and answer y when prompted ( or go here and read how to add key  (a ways down

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by Regenweald on 2009-05-17
Definitely use the ppa's, I did last night and was simply a matter of updating then installing through aptitude. Thanks to RVM for his hard work on the SMPlayer project.

---

