---
title: "ubuntu server installation problem"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-10-11
Hi,

I'm installing Ubuntu Server (x32, 9.04) on an old desktop of mine, I was planning on installing the OS on a new partition (keeping the existing windows partition intact) however, I've come across a problem when I'm installing it.

```

Your installation CD-ROM couldn't be mounted. This probably means 
that the CD-ROM was not in the drive. If so you can insert it and try 
again.

Try again to mount the CD-ROM?
```
The thing is, I've booted the installer from a USB memory stick with Unetbootin, and so obviously there isn't a CD in the CD drive! :/

Any help regarding this problem is much appreciated!
- Aaron.

---

### Post by keplerspeed on 2009-10-11
Why not just install from usb then and ignore mounting the cd drive?

So you can boot from usb but NOT boot from cd? When/where in the install are you getting this error? Does the cd drive work fine via live cd for example?

---

### Post by Letterbomb05 on 2009-10-11
Hi, thanks for your reply.

I simply mounted the ISO to my USB using Unetbootin on windows, then booted from USB on my server and followed the installation, I got passed the keyboard configuration and now I have this. My CD drive works fine, it's just that I don't have any spare CD's that I can write ubuntu to, so I have to use USB.

- Aaron.

---

### Post by keplerspeed on 2009-10-11
So when is asks "try to mount cd-rom" say yes. If it fails, thats ok just ignore it and continue the install without mounting the drive. Can you continue the install then?

---

### Post by Letterbomb05 on 2009-10-11
Hi,

if I ignore to 'detect and mount CD-ROM' the next option I have is 'Load installer components from CD'. I selected this however I get the same problem as before... Should I ignore it and continue to the next option which is 'Change debconf priority'?

- Aaron.

---

### Post by Letterbomb05 on 2009-10-11
I've heard on IRC that perhaps manually mounting the ISO on a loopback mount to my USB drive will probably fix my problem, if someone could please explain how to do this, it'd be much appreciated!

---

