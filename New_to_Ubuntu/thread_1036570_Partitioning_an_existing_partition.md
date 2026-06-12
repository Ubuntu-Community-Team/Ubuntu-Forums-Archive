---
title: "Partitioning an existing partition"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Jeezus on 2009-01-10
I'm running Hardy Heron on a Toshiba Satellite A105 laptop.
I'm trying to install a winXP VM with VirtualBox but am running into a problem.
I have my HDD partitioned into 3 sections one for swap, one for Linux, and one for media and data storage. virtualbox won't let me choose the location that it makes the partition for winxp in, and I don't have enough space on my linux partition for it. It will let me choose an existing image though. How can I create an HDD image so I can select it for use as my winXP partition?

---

### Post by whoop on 2009-01-11
Running xp (or any other os) on virtualbox will not create a real partition. It will create a virtual partition. This partition will just be a file on any of your existing partitions (it will save itself on your linux partition by default). So don't worry about partitioning your hard-drive for running operating systems inside a virtual manager.

---

### Post by Shazaam on 2009-01-11
You want to make an XP virtual machine. Is this an image (pre-built) of Xp or are you installing XP from a Microsoft cd?
If from a regular Xp cd you don't need to worry about any partitioning so do this...
1. Start VirtualBox.
2. On the main page choose "New".
3. Type in the name you want, under OS Type choose Windows, version XP.
4. Next screen choose your intended memory size (half of your actual installed ram is ok).
5. Next screen check "Boot Hard Disk/Primary Master", then click "New" (not existing).
6. Next screen choose "Dynamically expanding storage".
7. Next screen choose your virtual hard drive size, click "Finish".

A listing for your Windows vm should now be in the main VBox window. Now do this...
1. Highlight the XP vm, click "Settings".
2. In the Basic tab set your video memory size and enable experimental 3d acceleration if you want.
3. Go to the Advanced tab, set your vm boot order.
4. Left side choose "Hard Disks". enable SATA controller if you want but if you do you will need the SATA drivers for XP handy for install.
5. " " choose "CD/DVD-ROM", check "Mount CD/DVD Drive" click "Host CD/DVD Drive" and make sure your drive is listed.
6. " " go through the rest, enable/configure what you want then click "Okay".
Put the XP cd in the drive then click "Start" and you should be able to install. Once you get your virtual XP up and running shut it down, go back to Settings>CD/DVD-ROM. Change the drive to "ISO Image file", make sure "VBoxGuestAdditions.iso" is showing in the box then start your virtual XP. When you get to the XP desktop you should be able to install the Guest Additions (highly recommended).

---

### Post by Jeezus on 2009-01-11
I can't get past the formating of the file system when I try to install windows. It just keeps locking up every time.
ANy ideas?

---

