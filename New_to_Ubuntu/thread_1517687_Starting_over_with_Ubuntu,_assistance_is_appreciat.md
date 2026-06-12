---
title: "Starting over with Ubuntu, assistance is appreciated"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Balding360 on 2010-06-25
Hello, I'm new here and new to Ubuntu.  My 5 year old desk top is on it's last legs, its running Windows XP pro right now and it's so messed up that it's hardly usable anymore.  So I want to reformat and start over

I downloaded Ubuntu 10.04 and made a CD, but before I get to swapping OS's I would like a condensed guide of what hardware will still function once I install Ubuntu.

First off, my PC is a Gateway 3GB RAM 250GB+500GB hard drives (two separate drives) Pentium D 2.80 GHz dual core processor.

Second, I have a PNY verto geforce 7300gt graphics card.  (should I remove that till I find some drivers?  will it work at all with Ubuntu?)

I also have a wireless network card, but I don't have it's specs in front of me. (should I remove this as well?)


Now here's my big question.  I have two hard drives, a 250gb and a 500gb.  windows is installed on the 250 and the 500 is only used for storage (there are no programs installed there).  If I were to reformat the 250 and install Ubuntu there would I be able to access the second hard drive as I normally would, or should I move everything that I want to keep somewhere safe (external HDD)?


I'm a total newb to this, and I didn't want to spend all day searching for answers that I would likely not understand.

---

### Post by bodhi.zazen on 2010-06-25
That is a lot of questions =)

I suggest you start by booting the Ubuntu live CD and see what hardware is recognized.

If everything works, go ahead and install.

If you have a problem, post back what problem you have.

As you install take care you understand what the installer is telling you in terms of your partitions.

See:

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

[GraphicalInstall - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GraphicalInstall") 

Ubuntu will recognize your data partition, although if you are no longer going to use Windows I suggest you back up your data and re-format the data partition to ext4 , or any linux native file system you wish. This is because Linux can not always debug ntfs or fat partitions if you have problems.

---

### Post by empty_spaces on 2010-06-25
Since you have already made a cd (I assume it's a live cd), why don't you just pop it in and select the option to "try ubuntu without any changes to your computer". I'm not sure about the exact words, but that option should let you try ubuntu without making changes to your computer.
Once ubuntu is running from the LiveCD, you will be able to see which hardware works and which does not.
THe Nvidia graphics should be fine. Ubuntu should automatically prompt you to install a proprietary Nvidia driver after installation.
Ubuntu should also see the second HDD without any issues.

Running the **lspci **or **lsusb **commands in the terminal should tell you what wireless card you have.

---

### Post by Balding360 on 2010-06-25
I knew my machine was falling apart, but I've just discovered that my CD drive doesn't work.  *sigh*

---

### Post by Wim Sturkenboom on 2010-06-25
Be aware that Linux does not use drive letters but refers to disks as sda or hdb and to partitions as e.g. sda1, sda2, or hdb1

Further I strongly advise to make a backup of your data, just in case a mistake is made.

---

### Post by Thelasko on 2010-06-25
> **Balding360 said:**
> I knew my machine was falling apart, but I've just discovered that my CD drive doesn't work.  *sigh*

Are you sure it just isn't enabled under your computer's boot options?

See: [Boot Device Selection]("https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html")

---

### Post by Balding360 on 2010-06-25
I;m sure, I went ahead and started windows and when I looked at the CD drive it did not recognize the a disk was inserted.  It also made some grinding sounds when it was trying too play the disk. 

And I think I may go ahead and pull the second HDD out since I don't have money for an external right now.

---

### Post by oldfred on 2010-06-25
Will your machine boot a USB flash drive? If so that is an alternative.

---

### Post by bodhi.zazen on 2010-06-25
> **oldfred said:**
> Will your machine boot a USB flash drive? If so that is an alternative.

First, test the CD drive with a known good CD, ti may simply be a faulty CD.

If you wish to boot from a usb drive, see unetbootin, it runs on windows (as well as Linux).

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Balding360 on 2010-06-25
It's weird, the disk is good (worked on my laptop) and the CD drive  "worked" with another disk.  

I dunno, I think I'm going to wait till I get a new CD drive.

---

### Post by Balding360 on 2010-06-26
OK I should have a new Drive in a few weeks.  

Oh, yes, my wireless adapter is a Netgear 108 Mbps wireless PCI WG 311t

And should I plug my monitor into the onboard graphics until I find drivers for my graphics card (also should I remove the graphics and wireless cards until I find drivers for them?)

---

### Post by sukigenseki on 2010-06-26
I don't see any reason why you wouldn't be able to access your 2nd hard drive unless for some reason Ubuntu is not able to detect it, but it should just show up in the "Places" section on the top panel in Gnome. If it is just empty and used for storage it will just show up as another drive you can access, and it will be in whatever format that windows gave it (either NTFS or FAT).

---

### Post by Balding360 on 2010-06-26
I'm not really worried about Ubuntu detecting and accessing the HDD once Ubuntu is installed.  I just want to make sure I don't hit a wrong button while installing and losing all the data.

---

