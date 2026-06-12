---
title: "Help with formatting/reinstallation/backup"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-16
So I have decided I am going to get rid of Windows Vista entirely and just use Ubuntu on its own partition. My laptop has two physical drives - one has Windows and Ubuntu installed (using Wubi) and the second had all my photos/videos and music. 

I'd like preferably to install 8.10 and return to my original settings, you know with the wallpaper/panel settings/AWN manager/installed programs etc etc

What's the best way to do this? I have used "Simple Backup" to backup the following:

/var/
/home/
/usr/share/menu/
/etc/apt/sources.list
/usr/local/
/etc/

I have also backed up my Windows personal files that are on C: drive of course.

Once I have backed everything up, what's the best way to format C: drive? I have Ubuntu 8.10 on a USB pen drive so should I just boot with that and choose to format C: drive as an EXT3 partition and then install Ubuntu on to that new drive?

Then I can just install Simple Backup from the repositories and use the "Simple Restore" to restore from the file the program made on my external HDD.

Does this sound correct? I just want to check everything before I do anything drastic.

---

### Post by kestrel1 on 2009-03-16
I would suggest a seperate /home partition. That way if you decide to re-install you keep all your personal data & program settings (not the programs themselves, once they are re-installed it looks the same)
So you would have '/' '/home' 'swap'

---

### Post by humphreybc on 2009-03-16
So I have my C: and D: drives, C is being reformatted and D is not... how can I move my /home folder to D drive and then tell the new install of Ubuntu to point to it?

---

### Post by Dynaflow on 2009-03-16
If you're paving over the entire hard drive, you may want to consider trying an encrypted filesystem:  [http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml) & [https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)

---

### Post by humphreybc on 2009-03-16
Hmm I might look at that. Can you do that with 8.10 or just 8.04?

---

### Post by kestrel1 on 2009-03-16
/home would be a seperate partition, not a folder on a partition. What you could do is make part of your current D drive (remember C & D are a Windows thing) your /home partition & copy the files over after the install then merge the rest of D to your /home partition.
Am I right in thinking that you have two partitions currently on the one drive & that drive is 320gb?

---

### Post by Dynaflow on 2009-03-16
> **humphreybc said:**
> Hmm I might look at that. Can you do that with 8.10 or just 8.04?

It's been easy and semi-automated for all releases since at least 7.10, when I started doing it.  I recommend it highly.

---

### Post by Dynaflow on 2009-03-16
I also have two hard drives in my PC, and I have them separately encrypted with the /boot (unencrypted, separate partition), / (encrypted), and a ~/Multimedia (in the same encrypted logical volume as /) partitions on hda and /home and swap (both in an encrypted logical volume) on hdb.

See here for decent instructions:  [http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

---

### Post by humphreybc on 2009-03-16
Sweet as. I'm downloading the 8.10 Alternate CD atm (you can't do it with the regular CD as I already have a copy of that?) and i'll have to get my friend to burn it as my burner is dying... :(
> 
Am I right in thinking that you have two partitions currently on the one drive & that drive is 320gb?

Nope I actually have two physical drives, sda and sdb. sda has a big Vista partition, and two smaller Toshiba recovery partitions. sdb is just one big partition with all of my important media files on it. I plan to format sda and the toshiba recovery partitions and merge them all then install encrypted Ubuntu on sda while leaving sdb alone so I don't mess with my important files (although everything is backed up of course).

Just out of interest, does anyone know how much space Vista takes up compared to Ubuntu? I'm running short on HDD space which is one of the many reasons i've decided to say goodbye to Vista once and for all. I was going to keep it for Dreamweaver and Photoshop CS3, but now I have read that you can get these working under Wine quite easily so there seems no reason to have Vista sitting there doing nought! I've only booted into it about three times in the last four weeks that I've had Ubuntu...

---

### Post by kestrel1 on 2009-03-16
Vista takes up loads more HDD space than Ubuntu. the minimum HDD space for Vista is 15gb, just to install the basic system. Ubuntu would be happy with half of that & you could have loads more stuff installed. My systems root takes about 4gb of a 14gb partition /home is bigger of course, but this system is mature & has mostly everything I need installed.

---

### Post by Dynaflow on 2009-03-16
I would personally recommend backing your data up to an external device for the moment and encrypting both drives.  This will allow you to put swap onto sdb (it's always best to have the swap partition on a separate physical drive from /) and have swap and whatever else you're storing on sdb be encrypted (having an unencrypted swap partition is a great way to allow an attacker to severely compromise your encryption scheme).

---

### Post by humphreybc on 2009-03-16
> **Dynaflow said:**
> I would personally recommend backing your data up to an external device for the moment and encrypting both drives.  This will allow you to put swap onto sdb (it's always best to have the swap partition on a separate physical drive from /) and have swap and whatever else you're storing on sdb be encrypted (having an unencrypted swap partition is a great way to allow an attacker to severely compromise your encryption scheme).

Okay thanks I might do this when I have the time... my external HDD is as slow as a legless old lady so it takes around 4 hours to transfer 200GB of stuff haha.

---

