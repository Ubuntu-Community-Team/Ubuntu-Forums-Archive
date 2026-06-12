---
title: "Returning to Ubuntu"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Donnut on 2009-05-11
I have just used OSX for a long time but got a netbook, and installed ubuntu on it.  I can't believe how well everything works!  The last Ubuntu I used was 6.10.  So, now I find myself a linux newbie again.  My question, is everything now point and click or do I still need to update my sources.list to plat multimedia?

---

### Post by anjilslaire on 2009-05-11
Get medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It'll handle all of your media/codec needs

Otherwise, you're pretty much set.

---

### Post by jjacobs2 on 2009-05-11
You may not even need medibuntu anymore unless you want to play encrypted dvds.  First try ubuntu-restricted-extras and see if your files play with that version of the codecs or mplayer.  If you're into HTPCs you might want to read up on VDPAU as well.

---

### Post by Wiebelhaus on 2009-05-11
For multi media:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install libdvdcss2
```
```

sudo apt-get install w32codecs
```

or for 64bit

```
sudo apt-get install w64codecs
```

Search through add/remove and install any restricted packages you find there , the rest you'll find while your using the OS like flash can be downloaded from the link in firefox if you visit youtube.

---

### Post by Donnut on 2009-05-11
thanks alot.  this computer is amazing with Ubuntu!  Even the enhanced graphics like compiz work perfectly without tweaking now!  Linux is definitely easier to use by far than windows now.

---

