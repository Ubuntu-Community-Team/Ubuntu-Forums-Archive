---
title: "Installtion Partition question"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by c8n9b on 2009-10-02
Hey guys,

A friend suggested that I install Ubuntu so I'm going to check it out.  I went through the installation step but when I got to the partition section things got a little fuzzy.  It gave me the option of dual booting with Windows and that is what I selected.  Underneath that was a bar that let me dictate how much space to allocate for Ubuntu.  That is where I'm clueless.

What would be a good amount of space to allocate for Ubuntu?  Should I just allocate enough for the installation and then put the files in my partitions that my Windows machine runs on?  Or is the Ubuntu the only partition in which I can save files in while using Ubuntu?

Also I have another HD which has no OS on it that I use primarily for storage.  If I installed on that hard drive would I still be able to dual boot?

Thanks for your time guys,
Casey

EDIT: Whoops, I see I posted this in the wrong section, sorry Mods!

---

### Post by Paqman on 2009-10-02
> **c8n9b said:**
> 
What would be a good amount of space to allocate for Ubuntu? 


You'll need a minimum of about 6-8GB. I'd give it about 20GB if you've got the room.

> Should I just allocate enough for the installation and then put the files in my partitions that my Windows machine runs on? 

You can do that if you want. Or you could create a new partition and format it NTFS for storage use by both systems. End result is the same, but it's a bit tidier IMO. Bottom line: Ubuntu can read/write to all sorts of partitions, including Windows ones, but Windows can only read/write to NTFS or FAT partitions.

> Also I have another HD which has no OS on it that I use primarily for storage.  If I installed on that hard drive would I still be able to dual boot?

Absolutely.

Don't stress too much about partitioning. You can always modify it later. There's also a way to install that skips partitioning completely. Just boot into Windows, put your LiveCD in, select "install inside Windows" and tell it how much space you want to give Ubuntu. The installer (called [Wubi]("http://wubi-installer.org/")) will do some magic and set you up with a nice dual-boot system.

---

### Post by nhasian on 2009-10-02
if you have a whole other drive, the preferred method is to set aside a partition just for root / a separate one for /home, and one for swap.
having a separate /home partition makes it easier to backup or restore your data in the future.

---

### Post by Paqman on 2009-10-02
+1 for a separate /home partition, although the installer can't do this for you automatically. It would require manual partitioning. If that's a bit full-on for you at the moment, then don't worry it's not essential. It's just a very handy way to set your system up.

---

### Post by Bartender on 2009-10-02
> **c8n9b said:**
> Also I have another HD which has no OS on it that I use primarily for storage.  If I installed on that hard drive would I still be able to dual boot?

I assume this is an NTFS formatted HDD, and it has your personal data on it?  What's that personal data worth to you?  I'd recommend leaving that drive alone and finding a used one or buying a new one.  Transfer your personal data to the new HDD and use the older one to gain some experience with Linux partitioning and installation, or just use the new one for Linux.

Especially if you haven't gained some familiarity with the Linux partitioners.  I'd hate to have you wipe out your personal data.

---

