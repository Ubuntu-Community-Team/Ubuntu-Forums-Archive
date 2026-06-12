---
title: "Sansa e250 MP3 player doesn't mount in MSC mode."
date: 2009-09-24
forum: New to Ubuntu
---

### Post by diablo75 on 2009-09-24
I just got this MP3 player in the mail today and have found that it will auto-mount in Ubuntu when it's set to MTP mode, but when I copy files over to the device none of them are "seen" by the device (I believe MTP was intended to be used by things like Windows Media Player and the like).  When I set it to MSC mode, Ubuntu acts like it's not there, or if it knows it's there, doesn't attempt to mount it as far as I can tell.

I am able to copy files to it from Windows while in MSC and MTP mode (MSC being the prefered choice), but I would like to be able to do this from Ubuntu as well.

Anyone know how to fix this so it works?

---

### Post by Chronon on 2009-09-24
Check out this bug report and see if you can make sense of it.

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

Apparently, autodetection/automounting of MSC devices was broken by overzealous libgphoto2.  HAL tries to mount everything in sight as MTP, whether or not the device responds to MTP commands.  There are some workarounds posted in the bug report but it seems that none of them work for everyone.  I find it a sad state of affairs that MSC functionality has been compromised for the sake of Microsoft technology.  

Reportedly, the bug is fixed in Karmic versions of libmtp and libgphoto2.

---

