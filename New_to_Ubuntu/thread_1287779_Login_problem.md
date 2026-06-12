---
title: "Login problem"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by inter-m on 2009-10-10
I had just installed ubuntu 9.04 on my msi laptop. I did all the updates and restarted and when it boots up it's all fine until I reach the login screen then I get a black screen with strange lines on top and nothing responds.  Any help is apprecitated.

---

### Post by superdav42 on 2009-10-10
Do you see any part of the login screen or just this? It sounds like xorg isn't working correctly with your video card. Sounds like your only option is to boot into recovery mode (it's one of the options when you first start up you have like 3 secs to choose it) There was probably a graphics driver update that is causing the problem. Basically after booting into recovery mode you have to edit your xorg.conf and change the device driver to "vesa" than you should be able to boot in normal mode, except it'll be ugly until we figure out what wrong with the new driver.

---

### Post by orky7 on 2009-10-10
when ever u upgrade your graphic card drivers always backup the xorg.conf file so that if something wrong happens u get the previous working configuration......

---

### Post by sandyd on 2009-10-10
Press Ctrl+Alt+f1.
Login and type in
```

sudo dpkg-reconfigure xserver-xorg

```
```

sudo apt-get install dkms

```

The second command will ensure you dont have these problems in the future.

you will then have to install your graphics drivers... again...

---

