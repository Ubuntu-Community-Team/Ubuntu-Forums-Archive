---
title: "Replicating ubuntu install"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by mpledge52 on 2010-01-01
Hi all. 

I've bought a new hard drive and I want to replicate my linux partition and basically just dump it onto the new hard drive so I can carry on rather than having to re-install it all like I would with windows.

Currently I have 3 partitions on the hard drive; 1 for windows XP, 1 for ubuntu, and 1 for the swap space.

The ideal situation would be for me to do the following:

[LIST=1]
[*]Create an image file of the current linux partition and save on external hard drive
[*]Remove the hard drive and insert the new one
[*]Install windows XP on the whole disk
[*]Partition it so I have the 3 partitions as before
[*]Copy the image back onto the ubuntu partition and hey presto!
[/LIST]


I've had a read about a couple of methods, to do this.  dd and partimage.   Both look like they could do the job, but there seems to be a few more guides for using partimage so I might stick to that.  I have a few questions about the process though:


[LIST]
[*]I think I understand how to create the backup, but how do you restore it?  I presume you need to have ubuntu installed so you can access the terminal to run partimage in order to restore the image?  So do I just stick the ubuntu cd in and install ubuntu again as I did first time round, then run partimage which will just over-write everything?
[*]Does this handle the GRUB bootloader as well?  If not how do I get back into the ubuntu partition on startup?
[*]Do the ubuntu and swap partitions have to be the same size on the new hard drive?  I'll be keeping the swap size the same (2gb), but I'l make the ubuntu partition bigger by 20gb or so.  I think this is ok but just want to double check.
[/LIST]
Thanks very much for any help.

---

### Post by presence1960 on 2010-01-01
I recommend to use [clonezilla]("http://clonezilla.org"), much easier.

If you need to restore GRUB, it depends on which version of GRUB you have on MBR. Below is how to for both versions:

**_GRUB Legacy (version 0.97)_**

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**_GRUB2 (1.97 beta)_** see here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

P.S. you can save yourself some work if you have a windows install disk- not a recovery partition/CD/DVD. Partition the new hard disk before installing using [gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). Set up XP/Ubuntu partitons then boot the windows install CD to install to the NTFS partition you made for XP. When completed and you are ready proceed to use the Ubuntu image you made. That will save you having to defrag XP and resize it's partition. That's right I did say defrag. Some of the worst fragmentation on windows occurs after a new install. Don't believe me run the analyze disk function of disk defragmenter and you will see.

---

### Post by Pascal11110 on 2010-01-01
I would recommed clonezilla as well, but the live CD, not the server install. I use both at work for imagin large numbers of machines, and all clonezilla live needs to work is a Samba share (or a windows share) on the network that it can access and has enough space.

---

### Post by presence1960 on 2010-01-01
> **presence1960 said:**
> I recommend to use [clonezilla]("http://clonezilla.org"), much easier.

If you need to restore GRUB, it depends on which version of GRUB you have on MBR. Below is how to for both versions:

**_GRUB Legacy (version 0.97)_**

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**_GRUB2 (1.97 beta)_** see here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

P.S. you can save yourself some work if you have a windows install disk- not a recovery partition/CD/DVD. Partition the new hard disk before installing using [gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). Set up XP/Ubuntu partitons then boot the windows install CD to install to the NTFS partition you made for XP. When completed and you are ready proceed to use the Ubuntu image you made. That will save you having to defrag XP and resize it's partition. That's right I did say defrag. Some of the worst fragmentation on windows occurs after a new install. Don't believe me run the analyze disk function of disk defragmenter and you will see.

Just thought of this: unless your windows install is messed up you can image that with clonezilla as well. Or you can image the entire disk and put that onto your new hard disk instead of installing windows all over again.

---

### Post by tom.swartz07 on 2010-01-01
> **presence1960 said:**
> I recommend to use [clonezilla]("http://clonezilla.org"), much easier.

If you need to restore GRUB, it depends on which version of GRUB you have on MBR. Below is how to for both versions:

**_GRUB Legacy (version 0.97)_**

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**_GRUB2 (1.97 beta)_** see here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

P.S. you can save yourself some work if you have a windows install disk- not a recovery partition/CD/DVD. Partition the new hard disk before installing using [gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). Set up XP/Ubuntu partitons then boot the windows install CD to install to the NTFS partition you made for XP. When completed and you are ready proceed to use the Ubuntu image you made. That will save you having to defrag XP and resize it's partition. That's right I did say defrag. Some of the worst fragmentation on windows occurs after a new install. Don't believe me run the analyze disk function of disk defragmenter and you will see.

I just copied my drive two or three weeks ago. The newest version of Clonezilla asks if you want to copy your Master Boot Record, or in our case, GRUB.

---

### Post by Pascal11110 on 2010-01-01
I have never imaged hard drives with multiple OS's, but I have done many with multiple partitions (we put a backup partition on all the drives) and that works fine, so I think as long as you use the option to copy your mbr you should be fine.

---

### Post by mpledge52 on 2010-01-01
Thanks for the advice all.

Just had a look at CloneZilla, looks like it could do the job nicely.  I think I will use the save/restore parts rather than copying my whole hard drive as it might be an idea to clean off all the crud from my windows install anyway.

Found [this]("http://www.dedoimedo.com/computers/free_imaging_software.html") guide on how to use it, does that look fairly up-to-date, no wild new things I will have to deal with?

How does it handle partition sizes as well?  E.g. I'll make the image of a 20GB partition, but I will be restoring it on a 50GB, will that work ok or will I have to fidle after restoration to utilise the whole 50GB?

Thanks again.

---

### Post by Pascal11110 on 2010-01-01
Well you can bring it to a larger or smaller drive (as long as the there isn't more data than can fit on the smaller drive) but it is easier to a larger drive. Depending on the options you pick it can fill out your partitions to the entire size of the drive, but where you have multiple partitions, I think you should just move it to the new hard drive and then use pmagic to change the partition sizes.

---

### Post by VastOne on 2010-01-01
> **mpledge52 said:**
> Hi all. 

I've bought a new hard drive and I want to replicate my linux partition and basically just dump it onto the new hard drive so I can carry on rather than having to re-install it all like I would with windows.

Currently I have 3 partitions on the hard drive; 1 for windows XP, 1 for ubuntu, and 1 for the swap space.

The ideal situation would be for me to do the following:

[LIST=1]
[*]Create an image file of the current linux partition and save on external hard drive
[*]Remove the hard drive and insert the new one
[*]Install windows XP on the whole disk
[*]Partition it so I have the 3 partitions as before
[*]Copy the image back onto the ubuntu partition and hey presto!
[/LIST]


I've had a read about a couple of methods, to do this.  dd and partimage.   Both look like they could do the job, but there seems to be a few more guides for using partimage so I might stick to that.  I have a few questions about the process though:


[LIST]
[*]I think I understand how to create the backup, but how do you restore it?  I presume you need to have ubuntu installed so you can access the terminal to run partimage in order to restore the image?  So do I just stick the ubuntu cd in and install ubuntu again as I did first time round, then run partimage which will just over-write everything?
[*]Does this handle the GRUB bootloader as well?  If not how do I get back into the ubuntu partition on startup?
[*]Do the ubuntu and swap partitions have to be the same size on the new hard drive?  I'll be keeping the swap size the same (2gb), but I'l make the ubuntu partition bigger by 20gb or so.  I think this is ok but just want to double check.
[/LIST]
Thanks very much for any help.

I build several machines using the same footprint especially the same drive size.

I pop in the new drive into a current system and then use DD to transfer everything to the new drive and pop it in the new system and boot straight away.

---

### Post by mpledge52 on 2010-01-02
Ok I've made a copy of my whole hard drive using clonezilla.  I figured I can fiddle around and sort out my windows partition later.

I was just going to switch over the hard drives but i had a thought;  does the drive you are copying the image onto have to be formatted?  At the minute it is just one large NTFS partition that I used for storage purposes.  Will clonezilla handle this ok or should I wipe it first?

If it needs to be wiped, what the easiest way to do this?  Bearing in mind I can't boot to it as I only have cables for the one hard drive in my computer.  Presumably there is a way to do this with the windows XP/Ubuntu setup disks?

Thanks.

---

### Post by Pascal11110 on 2010-01-02
I image unformatted drives all the time, I just pop them out of the package, and toss them in the machine, and bring down the image. The only problem I have ever run into is you might need to use a pmagic disc to mark the partition as boot/active.

---

