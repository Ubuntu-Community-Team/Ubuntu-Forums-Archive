---
title: "Ubuntu 9.04 Netbook Remix"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by PeterCharles on 2009-05-16
I've no real knowledge about Linux but wanted to try Ubuntu on my Acer Aspire 1.
[SIZE=1]I've [/SIZE][SIZE=1]Ubuntu 9.04 Netbook Remix [/SIZE][SIZE=1][SIZE=1]on a USB pen drive and it works fine, except it tells be the pen drive is 1 Gb when it's actually 4Gb??

Any explanations please.
[/SIZE][/SIZE]

---

### Post by pauna on 2009-05-16
> **PeterCharles said:**
>  I've Ubuntu 9.04 Netbook Remix on a USB pen drive and it works fine, except it tells be the pen drive is 1 Gb when it's actually 4Gb??


Well, the UNR USB image is designed to fit USB sticks of 1GB, it may be that it ignores all space outside the 1GB on the stick. Right now I can't verify this since I used a 1GB USB drive for my UNR image.

Despite this, if you install UNR to a PC, it will recognize all the disks in the system and let you partition, format and install the disks as you choose.

---

### Post by Seishuku on 2009-05-16
I tried the netbook remix on my aspire one and effects didn't work and neither did compiz.  After that I did a clean install with the desktop version, and everything works fine and dandy.  Not worth it, in my opinion.

---

### Post by PeterCharles on 2009-05-16
> **Seishuku said:**
> I tried the netbook remix on my aspire one and effects didn't work and neither did compiz. 
Oh, as far as I could tell it worked fine on mine :confused:

It did occur to me that if I could partition the USB into 1Gb and the remainder, then I could put [SIZE=1]Netbook Remix on the first partition and then have access to the[/SIZE] second partition for other stuff?

---

### Post by PeterCharles on 2009-05-17
However it seems impossible to partition a USB pen drive.
Unless anyone knows a reliable way

---

### Post by NTpspE on 2009-05-17
What is the actual point in netbook remix over normal ubuntu?
Because to me it seems like turning a fully functional netbook, into a larger version of a mobile phone, as the desktop looks like the menu off my phone. 

Why was it even released? I'd much rather use normal ubuntu than nr, might just be my opinion, but what are the advantages of unr?

---

### Post by ugm6hr on 2009-05-17
> **PeterCharles said:**
> It did occur to me that if I could partition the USB into 1Gb and the remainder, then I could put Netbook Remix on the first partition and then have access to the second partition for other stuff?

*Installing* Ubuntu requires 4-6GB; 1GB is enough to run the LiveCD / LiveUSB, but this will always be annoyingly slow.

There are ways to use this with *persistence* (i.e. maintaining your settings etc), but I wouldn't bother.  The NBR is easily installed without a swap partition to achieve a fully functioning install on USB.  You will need the full 4GB though.  However, you can't install from and to the same USB; maybe consider installing to an SD card if you want to try it out?

---

