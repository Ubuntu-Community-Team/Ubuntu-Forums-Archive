---
title: "Trouble installing Adobe Flash in Firefox"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by Snowblood on 2011-07-01
Hi All,

I just instlalled Ubuntu 11.04 2 days ago and I dowloaded the Adobe Flash plugin for Firefox through the Ubuntu Software Center but it wouldn't install in Firefox because it said it was a corrupt file.  I redownloaded it and the same thing happened.  So I went to the Adobe website and tried to download Adobe for Ubuntu here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and a message came up saying 'This link needs to be opened with an application.  Send to' and it asks me to choose a folder.  How do I resolve this please?  

Thanks.


~ Snowblood

---

### Post by TeoBigusGeekus on 2011-07-01
Try
```
sudo apt-get install ubuntu-restricted-extras
```
It will install not only flash, but also java, codecs, microsoft fonts, etc.

---

### Post by Snowblood on 2011-07-01
Actually I've resolved this by installing Ubuntu Tweak and then installing Adobe Flash from that.  Thanks anyway!  

Btw just enabled wobbly screens- how fun! :p

~Snowblood

---

### Post by beew on 2011-07-01
Actually by far the best way would be to use the flash-aid addon for firefox, it downloads and install the latest flash, removes conflicting versions and optimizes it for your system (e.g activating hardware acceleration if your graphic card supports it) It is developed by Lovinglinux who is a member of this forum.

I am surprised that this addon is not better known.

---

