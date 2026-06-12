---
title: "dual operating system"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by gigabyte rookie on 2011-05-04
installed ubuntu 11 tried everything posted to get poker stars to load to no avail so i reinstalled windows 7.  I really like the ubuntu OS and want to run it next to windows 7 when i try to install it from the cd i made it automatically tries to do a clean installation on my hard drive.  I have never run ubuntu before so i guess you could call me an embryo.  any suggestions on how to install next to windows would be greatly appreciated.  I eventually want to run ubuntu as my primary OS but want to take it slower than jumping in headfirst....
please help ......

---

### Post by dozycat on 2011-05-04
I know one easy way:

Install first windows 7, after that use the live cd of ubuntu to resize the windows partition.
create a new partition for ubuntu.
And install ubuntu in that partition ubuntu.

[http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

that must help.

But maybe some can help you with out losing your actual installation of ubuntu.

---

### Post by underdog512 on 2011-05-04
If I were you, I would look into the [Wubi installer.]("http://www.ubuntu.com/download/ubuntu/windows-installer") It allows you to run Ubuntu within Windows, Sort of like a virtual machine. This may be a better way of getting to know Ubuntu than Hacking up your hard drive into to separate partitions.

---

### Post by oldfred on 2011-05-04
Have you used all four primary partitions. That is usually the reason it will only offer the erase drive option for automatic install as it cannot create a new extended partition for all the logicals required.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples lots of detail:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by withdean on 2011-05-04
Hi,  gigabyte rookie

You can see this:   [http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/)

I think it's easy as 1,2,3...   :)   hope it works

---

### Post by jramshu on 2011-05-04
You can use disk management in 7 to safely shrink your hard drive. Make sure you defrag, disk cleanup, etc. before you do it. There are several good tutorials out there that will walk you through it, and get rid of clutter to gain the most hd space for Ubuntu.

---

