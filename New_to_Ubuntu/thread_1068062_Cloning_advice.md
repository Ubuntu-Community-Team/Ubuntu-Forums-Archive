---
title: "Cloning advice"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Sir Jasper on 2009-02-12
I have Ubuntu (dual boot with windows) on a second dedicated 40 GB drive, partitioned as to: Linux Primary (36,555 MB) DOS extended (1,609 MB) and Linux Swap (1,609 MB).

I have ordered a 250 GB portable external drive and I ask:

(a)   I assume there is no point in cloning the Swap partition but does the DOS partition change and is a good idea to clone it or back it up?

(b)   I see there are free cloning programs which eliminate free space but my understanding (easily mistaken) is that the Linux Primary partition does not need defragmenting because information is spread throughout the disk. So is it necessarily a good idea to eliminate free space on cloning?

(c)    I am thinking of using Gparted to partition the new portable drive into say, eight partitions and need to know if any style and formatting is needed or if cloning to any partition will automatically take care of that?

(d)    Have I missed an important question?

My regards

---

### Post by supersonicdarky on 2009-02-13
Do you want to clone or image the drive? It seems like imaging is what you want. (Clone: make identical copy of drive, image: create a disk image from a drive).

To image a drive, it's easiest to use dd. Probably a good idea to do this from a live cd as you don't want the contents to be changing while it's imaging.

As root:
```
dd if=/dev/*disk* conv=sync,noerror bs=64K | gzip -c > /path/to/external/drive/image.img.gz
```
That command goes through the drive, byte by byte, copies it to a file and compresses it. Compression works really well with empty blocks as all they are just zeros.

[More info can be found here.](http://www.linuxweblog.com/dd-image)

---

### Post by ramjet_1953 on 2009-02-13
Hi, there! :)

You may also want to check-out CloneZilla.
It is available as as stand-alone iso that you burn to a CD and boot the system from.

Here is a link to the CloneZilla site:

[http://clonezilla.org/](http://clonezilla.org/)

Regards,
Roger :)

---

### Post by Sir Jasper on 2009-02-13
Hi again,

Guys,thank you for your time and advice, I have carefully studied the links you both provided and when my new portable drive arrives I will post again to let you know how it goes (though,it may take me a week or more to report back).

My regards

---

