---
title: "whats the best way to install?"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by paulXPS on 2010-07-08
Is there any difference in running Ubuntu from cd than installing on hard drive?

---

### Post by arochester on 2010-07-08
Yes. Running from a CD is slower than installing on the Hard Drive - and- you can't save your settings on the CD, when you can save them on the Hard Drive.

You can also install it on a USB stick, assuming your computer allows USB booting. If it is (magic word) PERSISTANT then you can save your settings. If it is not persistant then you can't.

---

### Post by paulXPS on 2010-07-08
O.K. thanks.  One more ?    How about Virtual Box vs hard drive install?

---

### Post by Paqman on 2010-07-08
Virtualbox is always going to be slower than a proper install, since you're running two operating systems at once. VBox installs also don't have access to the actual hardware, which means no 3D graphics (for example).

---

### Post by paulXPS on 2010-07-08
I see now why the graphics didnt work. OK whats the best way i could partition my hard drive for both ubuntu and vista, since I have never done it before and which version of ubuntu would be best?

---

### Post by Paqman on 2010-07-08
If partitioning is a bit of a foreign country and you already have Windows installed you can [use Wubi]("http://www.psychocats.net/ubuntu/wubi"). Just pop the Ubuntu disk in when you're running Windows and let it install from there. No partitioning required to get started. You can migrate a Wubi-installed copy of Ubuntu onto dedicated partitions later if you want.

If you want to partition the drive now, you can do it during installation. The installer will give you several options, one of which will be to install Ubuntu alongside Windows. Pick that one and drag the slider to decide how mush space you want to give each system. Take a backup of your Windows partition first, just in case, and give a it a defrag too.

Some people like to partion manually and create a separate /home partition, but that's a little bit further up the learning curve. We can give you detailed instructions if you want. Personally i'd save that one for October when the next version of Ubuntu comes out and you're looking at maybe reinstalling anyway.

As for versions, use the latest: 10.04 (Lucid Lynx). It's a Long Term Support release, which means you can either upgrade in six month's time, or wait two years for the next LTS. Up to you really.

---

### Post by Goolie on 2010-07-08
> **paulXPS said:**
> I see now why the graphics didn't work. OK whats the best way i could partition my hard drive for both Ubuntu and vista, since I have never done it before and which version of Ubuntu would be best?


My first time, when I booted into the CD I just followed the guide for installing Ubuntu.  it partitioned the drive for me and took care of all the crazy stuff I didn't want to deal with.  All I did was decide how much space to give Ubuntu and how much to give Windows.  Was super easy and pretty quick.

I didn't defrag or back-up my Windows 7 Partition however, although I had no problems, I see most people calling out that it should be done as a precaution.  

I guess I just live my life like there's no tomorrow.

Good luck!

---

### Post by paulXPS on 2010-07-08
Thanks for the help..

---

