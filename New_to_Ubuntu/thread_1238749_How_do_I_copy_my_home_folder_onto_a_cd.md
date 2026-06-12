---
title: "How do I copy my home folder onto a cd?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by jalehtor on 2009-08-12
I have been trying to figure out a way to do this now for three days. I want to dual partition with xp. I now have Ubuntu 8.1. I don't want to lose info...I'm a teacher with lesson plans, videos, pics etc in my home folder.

---

### Post by Schendje on 2009-08-12
You can use Brasero (Applications -> Sound & Video -> Brasero) to burn your files to a disk. You can also create an archive of all your files first, by selecting them and right-clicking, then choosing "Create Archive".

If you put a CD in the drive, a message should pop up asking what you want to do.

But there might be an easier way to install XP and keep Ubuntu intact, could you give a little more info?

---

### Post by zeroseven0183 on 2009-08-12
If you have a hard drive big enough, and I'm sure you do, try to repartition it using **GParted**. Once you create a new partition then you can load Windows in it. However, Windows will overwrite the existing boot loader, Grub without giving a notice. So in order to correctly set dual boot, you will need to follow the instructions stated here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by MyR on 2009-08-12
> **jalehtor said:**
> I have been trying to figure out a way to do this now for three days. I want to dual partition with xp. I now have Ubuntu 8.1. I don't want to lose info...I'm a teacher with lesson plans, videos, pics etc in my home folder.

With partitioning the risk of losing data is very small if you use gparted to resize your partition.  However it is always a good idea to have a backup.

Open you home folder and hit ctrl+h to show all files.  The hidden files contain settings for your programs that you can also burn to disc with brasero or similar.

If you're using burned media as your backup keep in mind that it is not always reliable and does deteriorate over time.

peace

---

### Post by jalehtor on 2009-08-12
Thank you. I'll attempt to burn the stuff onto a disc, then try GParted before dual partitioning, for which I will need SO much help it's not even funny. :(

---

### Post by MyR on 2009-08-12
Not to get too far ahead, but just pop in the Ubuntu live cd and gparted is already installed under system > administration > partition editor

peace

---

### Post by Bartender on 2009-08-12
The GParted LiveCD is the only way to go

[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

If I attached the screenshot correctly, you'll see the one to download.  Burn the download as an .iso to a CD (slowly, 4X or maybe 8X), then set your BIOS to boot from CD, pop the CD in the optical drive, and reboot.

The stand-alone GPLCD is much more effective than trying to partition from inside Ubuntu.  Especially since the partitioner can't manipulate mounted devices, one of which will be your Ubuntu installation.

As far your /home installation, can you just copy the entire folder to a thumb drive or external hdd?  

I bought one of those external hdd dock thingies (Vantec NextStar) and a 1TB HDD - it's turned out to be much handier than I thought.

---

### Post by jalehtor on 2009-08-12
> **zeroseven0183 said:**
> If you have a hard drive big enough, and I'm sure you do, try to repartition it using **GParted**. Once you create a new partition then you can load Windows in it. However, Windows will overwrite the existing boot loader, Grub without giving a notice. So in order to correctly set dual boot, you will need to follow the instructions stated here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I have a backup. I will attempt to move onto the partition as soon as I can put the kids to bed. Thank you.

---

