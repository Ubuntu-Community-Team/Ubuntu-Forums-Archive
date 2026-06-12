---
title: "removing windows and ubuntu dual boot to ubuntu alone"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by jhaycx on 2010-08-11
hi!
i'm planning to remove my windows boot and make it ubuntu alone...
can i make those windows drive combine with my /home dev?

is it possible to extend it? thanks!

---

### Post by Earl_Maroon on 2010-08-11
Yes, but beware that you could lose data in trying.

Use gparted, which you'll probably have to install. Using that, you should be able to delete the Windows partition and extend your /home partition over the freed empty space. No changes will be made until you select apply or make changes or whatever the button is. But once you do select this you cannot interrupt the process.

I have done this before with no issues, but I would suggest you back up anyway.

---

### Post by TNT1 on 2010-08-11
Easy. Just back up your data - external drive, pile of dvd's, whatever - wrtie down your settings for mail/wireless/whatever, stick in the distro of choice, format and install...

---

### Post by Zorgoth on 2010-08-11
If you are going to reinstall Ubuntu, here's some tips:

Back up all the hidden (things starting with a ., Ctrl-H in nautilus to view them) stuff in your home folder to get your settings and to save the packages installed on your computer, go to Synaptic Package Manager (System>Administration>Synaptic...) and under the File menu select - Save Markings as... and remember that before you save them, you should check the box that says "save full state, not just changes."  Back up this file, and with your installed applications and settings all saved, getting your system running again will be a breeze!

---

### Post by TNT1 on 2010-08-11
> **Zorgoth said:**
> If you are going to reinstall Ubuntu, here's some tips:

Back up all the hidden (things starting with a ., Ctrl-H in nautilus to view them) stuff in your home folder to get your settings 

dammit. I used a pencil and a piece of paper...

---

### Post by john newbuntu on 2010-08-11
If you can open up a terminal, type the command:
```
sudo fdisk -lu
```and post the output here, it will help.
Also list your /home partition and root partition.

---

### Post by jhaycx on 2010-08-11
here's the result in fdisk -lu command

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   266242047   133017600    7  HPFS/NTFS
/dev/sda3       266242048   418285898    76021925+   7  HPFS/NTFS
/dev/sda4       418287614   488396799    35054593    f  W95 Ext'd (LBA)
/dev/sda5       484263936   488396799     2066432   82  Linux swap / Solaris
/dev/sda6       418287616   481456127    31584256   83  Linux
/dev/sda7       481458176   484263935     1402880   82  Linux swap / Solaris

Partition table entries are not in disk order


since i'll be removing my windows... now i need to install vmware...

do you know a guide to do it?

also, my laptop is dual core, 2 gig in memory, will this slow my pc?

i need to install some big and serious programs there like MS SQL and and maybe Visual Studio... 

not for me to regularly used but just in case i'm in presentation where i can't bring my desktop at the place...

i just really want to stick with linux... open source lover! XD

---

### Post by john newbuntu on 2010-08-11
I'm sorry I have not installed vmware before.  You appear to have plenty of memory.  I do not think it will slow your laptop for most operations.  

As far as behemoth like MS SQL server and visual studio go, I am assuming you will be running these under wine/vmware/virtualbox in Ubuntu.  I strongly suggest that you try these in your current Ubuntu installation first before removing Windows.

You also do not require 2 swap partitions.  You could combine them both into one.

Should you decide to remove Windows and all NTFS data, you can delete partitions /dev/sda1, /dev/sda2 and /dev/sda3.  This will give you a good 200GB of space.  You can then create an ext3/ext4 partition as appropriate with this space and move your existing /home filesystem to this partition.

As suggested several times before, always make a backup of your existing install on /dev/sda6 and any other NTFS data you might require later on should you change your mind.

Psychocats have a good tutorial here to move /home to its own partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

