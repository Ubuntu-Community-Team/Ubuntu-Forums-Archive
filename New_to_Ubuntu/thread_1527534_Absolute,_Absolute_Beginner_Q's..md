---
title: "Absolute, Absolute Beginner Q's."
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Ian Daniel on 2010-07-09
Some quick Q's and help required for an absolute, absolute beginner if anyone is interesting in helping.

I'm not technical, but i work more on the frontline so to speak: ecommerce, SEO, usability, etc. But I have to say this place is bl**y confusing, its schizo, but Ubuntu looks good so any help would be massively appreciated.

1) PC or Netbook version for a 17" laptop?

2) Is there a basic install guide with details how to set up a partition and install Ubuntu?

3) Where do you recommend installing Ubuntu for ease of use and transfer should i move over to a new PC say in 12 months time. Is it better to dump this on an external HD or on my internal HD. Again so i can move it to a new PC in the future.

4) What size is the OS?

Thats it for now guys.

Appreciate any responses
Ian

---

### Post by LowSky on 2010-07-09
1. Go with the PC version, the netbook version is made for screens sizes under 12"
2. YES, [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
3. Remember this is an operating system, a new PC will have diffesrent drivers and settings and may cause issues if you do something wrong. The best advice is to save all personal data to a external drive so you have it as a backup.
4. What Size is the OS?  A full install without additial packages is  under 6GB. My current install takes up less than 15GB.

---

### Post by Rubi1200 on 2010-07-09
> **Ian Daniel said:**
> Some quick Q's and help required for an absolute, absolute beginner if anyone is interesting in helping.

I'm not technical, but i work more on the frontline so to speak: ecommerce, SEO, usability, etc. But I have to say this place is bl**y confusing, its schizo, but Ubuntu looks good so any help would be massively appreciated.

1) PC or Netbook version for a 17" laptop?

2) Is there a basic install guide with details how to set up a partition and install Ubuntu?

3) Where do you recommend installing Ubuntu for ease of use and transfer should i move over to a new PC say in 12 months time. Is it better to dump this on an external HD or on my internal HD. Again so i can move it to a new PC in the future.

4) What size is the OS?

Thats it for now guys.

Appreciate any responses
Ian

1) PC version

2) [http://members.iinet.net/~herman546/index.html;]("http://members.iinet.net/%7Eherman546/index.html;") [https://help.ubuntu.com/community/HowtoPartition;](https://help.ubuntu.com/community/HowtoPartition;) [http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)

3) as suggested above and below

4) Default install (not adding anything in) is under 4GB

Good luck and welcome!

---

### Post by Paqman on 2010-07-09
> **Ian Daniel said:**
> 
1) PC or Netbook version for a 17" laptop?


PC

> 2) Is there a basic install guide with details how to set up a partition and install Ubuntu?

[http://ubuntu-manual.org/]("http://ubuntu-manual.org/")

> 3) Where do you recommend installing Ubuntu for ease of use and transfer should i move over to a new PC say in 12 months time. Is it better to dump this on an external HD or on my internal HD. Again so i can move it to a new PC in the future.

I wouldn't use an external drive. Running your OS over USB would be slow. You could either image your current install onto your external to do the transfer (check our Clonezilla LiveCD for this) or you could just back up your data and settings and reinstall. Both are pretty easy, the latter is probably quicker.

> 
4) What size is the OS?


Round about 3-4GB for a fresh install I think. You'll probably want at least 10GB, more if you ever work with large temp files (eg: authoring DVDs)

---

### Post by audiomick on 2010-07-09
> **Ian Daniel said:**
> 
1) PC or Netbook version for a 17" laptop?
PC version. The main difference, as far as I know, in the netbook version is a visual optimisation for small screens, and maybe a couple of other doodads.

> 2) Is there a basic install guide with details how to set up a partition and install Ubuntu?

Are you wanting to set up a dual-boot?
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
or just Ubuntu
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

> 3) Where do you recommend installing Ubuntu for ease of use and transfer should i move over to a new PC say in 12 months time. Is it better to dump this on an external HD or on my internal HD. Again so i can move it to a new PC in the future.
If you want to make a migration, all you basically have to do is take your /home folder with you. All of your system settings and stuff are in there. It is also not a bad idea to create a separate partition for /home when you install. Should you have to re-install for any reason, you can simply re-mount the /home partition during the install, and you're back in business. There is info on partitioning here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

To create a separate /home during installation, you need to choose the "manual" option when the installer gets up to the partitioning stage.

> 4) What size is the OS?
The system itself takes up under 5 GB, I think.  This machine has 7GB in it's system partition, after about 3 years. I have a netbook with a fresh Netbook Edition on it that has 3.5GB in the system partition.

A suitable partition scheme would be:
about 10GB mounted at / for the system
a swap partition a bit bigger than your RAM if you want suspend to work. Otherwise, about a gig should do.
the rest mounted at /home.

A further refinement for a dual boot system would be to keep /home small (maybe 10GB, although I have read posts from people who say the only have 1 or 2 for /home) and the rest of the space for data storage as an NTFS partition so that you can access your data from windows as well.

There is also a lot of good reading here
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Ian Daniel on 2010-07-09
Thank a lot for the rapid reply guys. I'm going to have a read through your responses in the morning and post any more Q's i may have. I've managed to set up a partition for this os in Windows 7. Easy when you know how.

Can I ask a Q... is there a comparison/explanation/differences between these 3 systems? 

ubuntu/kubuntu/xubuntu 

Thanks
Ian

---

### Post by audiomick on 2010-07-09
Hi.
The difference revolves around the default desktop. Ubuntu uses Gnome
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

kbuntu uses kde
[http://en.wikipedia.org/wiki/Kde](http://en.wikipedia.org/wiki/Kde)

and xubuntu uses xfce
[http://en.wikipedia.org/wiki/Xfce](http://en.wikipedia.org/wiki/Xfce)

The different desktops bring different packages with them, and different default applications for some things. Between Gnome and KDE, the choice is largely a matter of personal preference. Xfce is supposed to be lightweight, although I have read that Xubuntu is not particularly lighter that Ubuntu or Kbuntu.

---

### Post by Sir Jasper on 2010-07-09
Hi,

My suggestion is to try Ubuntu 10.04 for three reasons:

(1) It is by far the most used with a specific and comprehensive Manual included within the OS or downloadable as a separate pdf (which it would doubtless be a good idea to skip read soon).

(2) Since it is the most used you may get a little faster help if you have questions to ask here.

(3) If you get used to Ubuntu for 2 or 3 months you could easily add an Xubuntu and/or Kubuntu desktop to try either or both from within Ubuntu (and you could easily uninstall either or both if you wanted to).

I am not sure if you are going for Wubi (Ubuntu within Windows) or a Dual Boot (which I suspect most users would favour).

My regards

---

### Post by rwthelegend on 2010-07-09
> **Ian Daniel said:**
> Thank a lot for the rapid reply guys. I'm  going to have a read through your responses in the morning and post any  more Q's i may have. I've managed to set up a partition for this os in  Windows 7. Easy when you know how.

Can I ask a Q... is there a comparison/explanation/differences between these 3 systems? 

ubuntu/kubuntu/xubuntu 

Thanks
Ian
Use Gnome (aka plain Ubuntu), KDE is buggy and slower and xfce is sort of a lightweight gnome for old comptuers.

---

### Post by jtarin on 2010-07-09
> **rwthelegend said:**
> Use Gnome (aka plain Ubuntu), KDE is buggy and slower and xfce is sort of a lightweight gnome for old comptuers.
You should qualify that statement with factual information rather than personal experience as mine is radically the opposite as I'm sure are others.

---

### Post by bodhi.zazen on 2010-07-09
> **rwthelegend said:**
> Use Gnome (aka plain Ubuntu), KDE is buggy and slower and xfce is sort of a lightweight gnome for old comptuers.

IMO you should select the version of Ubuntu based on which DE you prefer

KDE = kubuntu
Ubuntu = Gnome
Xubuntu = XFCE

IMO performance is not all that different across these window managers and, again IMO, neither of the 3 is in any way better for "old computers".

For old computers it is best to do a minimal install and install only the applications you need and to use light weight apps (gedit rather then OpenOffice) as much as possible.

slitaz is a much better OS for old computers.

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

