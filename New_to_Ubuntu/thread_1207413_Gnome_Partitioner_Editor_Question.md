---
title: "Gnome Partitioner Editor Question"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by mikodo on 2009-07-08
Hello everyone,

I want to do my first ever partitioning of my hard drive in preparation for upgrading Ubuntu. I have settled on Gparted, as it is a supported app. in Ubuntu. While reading online about this; one author suggests the Live CD of Gparted as follows:

"for example, GParted is available in the Ubuntu repositories -- but it's pretty useful to have on a live CD that lets you make changes to all the partitions without worrying about having any of them mounted".

Which of these versions of Gparted do you recommend? Or does it really matter?

I have no intention of dual booting into any other OS's (if that makes any difference in your responses).


Thanks again.

---

### Post by carml on 2009-07-08
You can you a Live of Ubuntu or Gpated Live,they should work in the same way. :)

---

### Post by credobyte on 2009-07-08
Both versions are +/- equivalent - use whichever you want/can ;)

---

### Post by alexlafreniere on 2009-07-08
The Ubuntu LiveCD includes GParted, just boot into the LiveCD and it gives you a full GParted installation ready to go. All of your partitioning can be done at install time.

---

### Post by Mark Phelps on 2009-07-09
The GParted LiveCd tends to contain a newer version than the ones bundled with the distros, but apart from that, they are identical in function.

---

### Post by az on 2009-07-09
If you are going to partition the drive on which you are currently running Ubuntu, then you need to run from a live CD.  You can't partition a drive with a mounted partition on in.

---

### Post by mikodo on 2009-07-10
> **az said:**
> If you are going to partition the drive on which you are currently running Ubuntu, then you need to run from a live CD.  You can't partition a drive with a mounted partition on in.

Thank you for stating this. I intend to use the one OS (Unbuntu) and as you stated, to be able to partition this drive I do indeed need to use the Live CD. This I confirmed with GParted developers on their forum and Web pages. I should have posted this in this thread for others to be aware of. And yes, the Live CD iso is the current stable version (Gparted 0.4.5-3) which has quite a few more features than the one in Ubuntu 8.04 repositories.

mikodo

---

### Post by egalvan on 2009-07-10
> **mikodo said:**
> Thank you for stating this. I intend to use the one OS (Unbuntu) and as you stated, **to be able to partition this drive I do indeed need to use the Live CD.** This I confirmed with GParted developers on their forum and Web pages. I should have posted this in this thread for others to be aware of. And yes, the Live CD iso is the current stable version (Gparted 0.4.5-3) which has quite a few more features than the one in Ubuntu 8.04 repositories.

mikodo

gparted locks partitions that are mounted; there is no way to damage an "in-use" partition.
Unless you force an "un-mount".

I regularly use (and support $$) partedmagic.
(partedmagic.com)
A full distro in it's own right. Has more partition tools, and boots faster than Ubuntu LiveCD.

---

### Post by mikodo on 2009-07-10
> **egalvan said:**
> gparted locks partitions that are mounted; there is no way to damage an "in-use" partition.
Unless you force an "un-mount".

I regularly use (and support $$) partedmagic.
(partedmagic.com)
A full distro in it's own right. Has more partition tools, and boots faster than Ubuntu LiveCD.


Just to be accurate, I was talking about the GParted Live CD and booting it from an usb stick or such.

---

### Post by Bobber47 on 2009-07-10
Gparted is very reliable.  I've resized numerous NTFS partitions during Linux installs from the LiveCDs (of Ubuntu or other distros) and never encountered any errors in subsequent usage (Win will do a disk check, but then proceed normally).  If the resized partition is large, it might take several hours, and Gparted doesn't always give you clear signs of progress, but it has always worked - just don't interrupt it - let it finish!

---

### Post by earthpigg on 2009-07-10
beware: windows _**vista**_ (not xp, 2k, etc) has been reported by several people not to respond well to having its partitions altered by non-windows tools.

---

### Post by mikodo on 2009-07-10
> **earthpigg said:**
> beware: windows _**vista**_ (not xp, 2k, etc) has been reported by several people not to respond well to having its partitions altered by non-windows tools.

Thank you. I still have a copy of Vista around somewhere and had entertained playing with it in a partition maybe sometime. The heck with it, I never liked it in the first place. Maybe I'll just test it as a Frisbee.

---

### Post by egalvan on 2009-07-10
> **mikodo said:**
> Just to be accurate, **I was talking about the GParted Live CD and booting it from an usb stick or such.**

I figured you were talking about the gparted distro...
Thing is, I haven't used it in the last year since I discovered partedmagic...
The last time I used gparted Live, it was basically a partition editor... nothing else.
So since I had no recent experience with it, I decided to compare it to something i did know, and that most folks are using... an Ubuntu LiveCD.

PartedMagic is a rather full-featured distro...
web tools, file managers, cloning tools, photo recovery,
a nice graphical desktop...
It's a small download, aprox 95M..
it boot fast.
I have both a CD and a USB always on hand.

Main reason I changed from gparted to partedmagic was the ability to read and write NTFS and ext2/ext3 partitions,
 and move files around using a graphical Linux front-end.

In the end. we have a great choice in our software.
It's part of what makes Linux great! :)

P.S.
reading a post similar to this one is what led me to try partedmagic.

---

### Post by mikodo on 2009-07-10
Re: PartedMagic

Thank you for your replies. I'll be certain to give it close scrutiny also.

---

