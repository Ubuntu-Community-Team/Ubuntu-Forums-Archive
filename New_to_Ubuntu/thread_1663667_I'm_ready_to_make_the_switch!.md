---
title: "I'm ready to make the switch!"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by cbennett926 on 2011-01-09
Hello, I currently use WUBI with my Windows Vista. I'm am going off to college this September and would love nothing less to go off with Ubuntu on my laptop. I love Ubuntu, but still want to have Windows, for games and such; how do you suppose I go about this?

What kind of laptop do you propose?

Can I run a full Ubuntu installation on my Seagate External Harddrive? 

Does WUBI count as an  Ubuntu user, or am I just a noob show off?

---

### Post by wojox on 2011-01-09
I would uninstall wubi from inside Vista. Then defrag Vista. Shrink Vista's volume to make room for Ubuntu. Install Ubuntu on new space.

Wubi is really to try out to see if you like Ubuntu. I wouldn't use it for long time use.

---

### Post by DanPiazza on 2011-01-09
I used WUBI for a few weeks before releasing the performance is much better when Linux has its own dedicated partition. Just create a second partition for Linux and then duel boot.

---

### Post by Bucky Ball on 2011-01-09
+1 to everything mentioned. Addressing your point about external hard drive install; that will work with a little tweaking BUT if you have only a USB connection that is going to slow you down. ;)

Wubi is like some medication; don't use over an extended periods! lol

There's no *real* reason not to but you don't get the full experience. A full install is MUCH better. :)

---

### Post by cbennett926 on 2011-01-10
Well, now I'm really gonna sound dumb, can anyone walk me through creating a new partition? Also, is there anyway to undo a partition as this isn't technically my computer.

---

### Post by Bucky Ball on 2011-01-10
This will help:

[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

Another walkthrough, probably better than the first link, here:

[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)

Go to 'Hard Disk Partitioning' down the page a bit then to the section further down: [U]Here's how you do a manual partitioning with /home:

[/U]ps: Absolute beginner talk forum; all questions welcome! There is no dumb question here (within reason). ;)

---

### Post by mastablasta on 2011-01-10
to the first part have a look here: 
how to create partition in windows: [http://windows.microsoft.com/en-US/windows-vista/Create-and-format-a-hard-disk-partition](http://windows.microsoft.com/en-US/windows-vista/Create-and-format-a-hard-disk-partition)
how to install ubuntu: [http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/)
 
second part - partitions can later be deleted and free space added to another partition.

---

### Post by mikewhatever on 2011-01-10
> **cbennett926 said:**
> Well, now I'm really gonna sound dumb, can anyone walk me through creating a new partition? Also, is there anyway to undo a partition as this isn't technically my computer.

If the computer is not yours, you probably should get an explicit permission from the owner first. Partitioning, installing operating systems is best suited for your own hardware. Having a good recovery strategy wouldn't hurt either.

---

### Post by Bucky Ball on 2011-01-10
+1  to that and esp recovery strategy.

---

### Post by cbennett926 on 2011-01-10
So, maybe I should wait until I get a laptop, and until then use wubi?

---

### Post by abdulapopoola on 2011-01-10
Just go ahead if the computer is yours. Ubuntu is so much fun and you get to learn a lot too.
Once you've gotten the hang of it, you won't want to ever go back to Windows.

Open source rocks!!!
[http://abdulapopoola.wordpress.com](http://abdulapopoola.wordpress.com)

---

### Post by mike555 on 2011-01-10
I would not recommend wubi install, have someone help you do a real install on a separate partition , that way when Windows takes a dump you still have Ubuntu .......
 if Windows messes up and you have Ubuntu installed "in" Windows (wubi), who knows what will happen , you might not be able to boot at all ...

---

### Post by oneindelijk on 2011-01-10
Hey, 
If you're waiting on your laptop, why not make a persistable pendrive with ubuntu on it ?
You can already set up your own profile on the stick and later when you have your own pc, install it immediately with the pendrive, copy over your ~ folder and what you've customized so far will be available right away.
Be carefull to use a stick large enough (4 Gb) and set the size of the persistent part to 1-2 Gb if you want to set up another profile and install additional software on the stick.
Good luck Ubuntuing !!

(oh btw a persistable pendrive, you can make through System - Administration - Start Up Disk Creation)

---

### Post by Bucky Ball on 2011-01-10
> **abdulapopoola said:**
> Just go ahead if the computer is yours. Ubuntu is so much fun and you get to learn a lot too.
Once you've gotten the hang of it, you won't want to ever go back to Windows.

Open source rocks!!!
[http://abdulapopoola.wordpress.com](http://abdulapopoola.wordpress.com)

OP clearly states it is 'technically not' their machine. Please read *whole* thread, not one post.  ;)

> **oneindelijk said:**
> Hey, 
If you're waiting on your laptop, why not make a persistable pendrive with ubuntu on it ?


+1. This is a good option until you get your own machine. When you do you will already know the ropes as you'd have learnt some about Ubuntu. Why wait? :)

---

### Post by cbennett926 on 2011-01-11
Can I use a USB External Hard Drive instead of a flash drive? Also, can I use 10.10 or 10.04?

---

### Post by oneindelijk on 2011-01-11
You can use any version of Ubuntu (at least from 8.04 and up, to my knowledge).
Many other distros also offer a live-cd which can be turned into a persistent flash drive (which can also be on an external drive as long as the computer you use supports booting from usb (you might need to enable this in the computer's bios).
Most modern computers have a boot menu that can be accessed through either F12 (HP,..) or F9 (Acer,..)

---

### Post by bcbc on 2011-01-11
> **cbennett926 said:**
> Can I use a USB External Hard Drive instead of a flash drive? Also, can I use 10.10 or 10.04?

Yes. You can [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") your current wubi install to an external hard drive, installing the grub2 bootloader on the external. As long as the computer supports booting from the USB drive this will work well without any change to the internal hard drive - with the benefit that you keep your current settings/programs/data from your wubi install.

---

### Post by Bucky Ball on 2011-01-11
External USB drive fine. I would recommend 10.04 LTS. 10.10 has some issues at the moment and you could well find some major (and minor) headaches unless you're lucky. ;)

Also 10.04 LTS (long term support) has MUCH longer support life (til April 2013).

---

