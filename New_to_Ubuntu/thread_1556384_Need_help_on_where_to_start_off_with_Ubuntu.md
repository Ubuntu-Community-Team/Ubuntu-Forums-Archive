---
title: "Need help on where to start off with Ubuntu"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by flyinghigh94 on 2010-08-19
Hello, im a really new person to Ubuntu and so am a little confused by it. I have a sony vaio laptop that has 1 hard drive with 2 partitions however I was going to skrink 1 of these by 20GB to put Ubuntu on. Is this goning to be enought space and should i do this in windows 7 disk manager? 

Also I am very confused with Grub as I dont really understand what it does and if it will not allow me to boot into windows after ubuntu has been installed. 

sorry for the really noobish questions and any help would be really kind thanks!:D

---

### Post by flyinghigh94 on 2010-08-19
any help please

---

### Post by pxr on 2010-08-19
I'd say go for it.

Download an ISO for Ubuntu 10.4 - I've installed it on some 4 machines in the last week or 2 and it 'just works' on all of them.

Anyway if you download and burn it to a CD you can try it 'Live' running from the CD with no changes to your system.

To answer your questions

One of the machines I installed Ubuntu on was an ASUS eeepc with a 4GB drive, it installed in 2.5GB so 20GB is more than enough

Let Ubuntu do the disk partitioning for you, if you decide to install you'll come to a screen that asks you where you want to put Ubuntu, it'll resize your partition & install itself in the newly created partition.

GRUB is a bootloader, so yes it will give you the option of booting into window$ after the install

---

### Post by oldfred on 2010-08-19
Yes you should use the windows 7 tools to shrink the windows partition and reboot once or twice to make sure windows is ok with its new size. 

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

Older but similar:
Dual Boot win/Ubuntu
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")
[URL="http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu"]
[/URL]

---

### Post by bbqsandwich on 2010-08-19
Be careful -- if you use Ubuntu to auto-detect your partitions, make sure it does not detect the 7-8 GB recovery partition as the main Windows installation or it might install itself over your Win7 partition.

---

### Post by candtalan on 2010-08-19
Use windows  to resize the partition, and yes 20GB is plenty enough space.
However, it is very much more straightforward to leave that 20 GB space as un partitioned. Do not create a new partition in the 20 GB space, leave it totally unused.

Then use the Ubuntu (desktop) CD to install Ubuntu. When it gets to the installer partitioner stage, you will see various choices. Carefully choose the choice which ofers to install Ubuntu into the 
'largest unused space on the drive'

Then let it continue

notes
1) I trust you have a good backup of your Windows stuff?

2) It is good to run the Live CD before you finally move to do an actual install. This is because if there are any problems, you will see them at the live CD stage, and you can prepare solutions then, and install later.

---

### Post by Jazzy_Jeff on 2010-08-19
As stated above, make sure all your stuff is backed up.

---

