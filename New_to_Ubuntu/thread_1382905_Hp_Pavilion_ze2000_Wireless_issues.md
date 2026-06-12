---
title: "Hp Pavilion ze2000 Wireless issues"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by lmg444 on 2010-01-16
Hi folks


I am trying to set up a friend's HP Pavilion ze2000.  Installed Ubuntu 9.10 without a hitch.  However, the wireless card doesn't work / no wireless connections.

I saw in some other threads some discussions about broadcom wireless cards, etc...but then people started talking about 'hardy' and such and lost me.  

Is there a link to a walkthrough and/or can somebody help me with this?

thanks!

kiva

---

### Post by bkratz on 2010-01-16
If you know what Broadcom card you have

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by yeats on 2010-01-16
Hi,

There was some bugginess with Broadcom drivers.  My own issue was solved by installing the bcmwl-kernel-source package.

> I saw in some other threads some discussions about broadcom wireless cards, etc...but then people started talking about 'hardy' and such and lost me.

Hardy Heron is the name of Ubuntu 8.04 LTS, which is the oldest version of Ubuntu currently supported.  I would recommend *not* following advice intended for Hardy and look for advice for Karmic 9.10 only.  Much has changed!

---

### Post by lmg444 on 2010-01-17
> **bkratz said:**
> If you know what Broadcom card you have

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

that linked did the trick.  I didn't actually know  what card I had, but it helped me figure out how to activate the driver, so it appears to be good now...

thanks!!!

---

