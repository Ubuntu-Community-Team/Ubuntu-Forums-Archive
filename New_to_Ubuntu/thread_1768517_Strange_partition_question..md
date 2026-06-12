---
title: "Strange partition question."
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Ladikn on 2011-05-26
Alright, to give a little background on my problem (to make it easier to understand...)

I've used windows for most of my life, tryed kubuntu for a bit but didn't have time to learn it so went back to windows.  I decided to give Ubuntu a shot, so I found a few pdfs about Linux and Ubuntu, and loaded Ubuntu onto my second partition (that I normally use for file storage).  I know it's weird, but I use the C: partition for file storage, and D: for windows, so Ubuntu is on my C: drive, along with most of my files.

Now, Ubuntu is working, I'm online in it now, but I can't access the rest of my C: (file) drive, just my "File System", which has all my Ubuntu files in it.  I could just move all my files into there and work with it, but I was wondering if I could mount my partition that's running Ubuntu to be able to access it's files.  

When I tryed ""# sudo fdisk -l" this came up.

----------------
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03000300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9728    37182442+   f  W95 Ext'd (LBA)
/dev/sda5            5100        9728    37182411    7  HPFS/NTFS
----------------

which /dev/sda1 is my C: (file and Ubuntu) partition.  So I tryed...

sudo mkdir -p /media/c
sudo mount -t ntfs -o iocharset=utf8,umask=000 /dev/sda1 /media/[FONT=Verdana]c

and I got this error.

------------------------
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
------------------------

Now, I'm guessing that's because it's the partition I'm booting Ubuntu from, but I can't access any of my other files from there.  Is there a way for me to get to those files without moving them into the Ubuntu folder?  (which would mean updating all my links and shortcuts in windows)

P.S. If your wondering why I use such a weird file system, or why I don't just use Ubuntu in it's own drive, I have a new computer half built and am trying to keep my files to transfer when it's finished, and am trying Ubuntu to see if I want to make it my main OS on my new computer.

TL;DR, How do I mount the partition that Ubuntu is loaded in, or at least access files from it?
[/FONT]

---

### Post by yetiman64 on 2011-05-26
I suspect from the fdisk output you have done a Wubi install.  Is this right ?

> The Windows partition where you installed Wubi is available as /host  within Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media From this link, [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

Hopefully this might help you find the files you want.

---

### Post by dFlyer on 2011-05-26
sda1 only shows a windows fs. I don't see any linux fs in the partition. Are you running ubuntu through windows?

---

### Post by Ladikn on 2011-05-26
Hmmm, I did use Wubi I think.  I just downloaded the Ubuntu installer from the website, opened it up in windows, and loaded it onto my secondary partition.  However, I'm not actually running it in windows, I'm running it by itself.

I loaded GParted to try to get a better look at my partitions, and sda1 is my Ubuntu/file partition, sda5 is windows.  Honestly, the only way I can tell though is the free space in the drives.

Would it work better if I took Ubuntu out of that partition and loaded it into the same partition as Windows?

---

### Post by yetiman64 on 2011-05-26
> **Ladikn said:**
> Hmmm, I did use Wubi I think.  I just downloaded the Ubuntu installer from the website, opened it up in windows, and loaded it onto my secondary partition.  However, I'm not actually running it in windows, I'm running it by itself.

I loaded GParted to try to get a better look at my partitions, and sda1 is my Ubuntu/file partition, sda5 is windows.  Honestly, the only way I can tell though is the free space in the drives.

Would it work better if I took Ubuntu out of that partition and loaded it into the same partition as Windows?

Wubi installs run Ubuntu from within a file on the Windows NTFS filesystem, hence the fdisk output you posted earlier. The grub bootloader is used, but is not booting Ubuntu from its own partition like "normal" separate partition installations of Ubuntu.

No, it is actually best, performance wise to install Ubuntu to its own partition altogether. Wubi is good for a short term test, but for day to day running of Ubuntu a complete partition install is best. You would need to consider repartitioning your hard drive from the live cd and installing Ubuntu again. It is possible to migrate a wubi install to a partition but is a complex process.

Here is another link for information : [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Note the link re migrating at the end of the first post there.

---

### Post by Ladikn on 2011-05-27
*sigh* Ah well, thanks for your help.  I've been looking over those links, and I don't think I'll be able to get this working, since it won't go past the Ubuntu file system in the partition.  I could just move the files I need into Ubuntu and deal with it.  Thanks for your help!

---

### Post by oldfred on 2011-05-27
Someone else with similar questions:

[http://ubuntuforums.org/showthread.php?p=10821011](http://ubuntuforums.org/showthread.php?p=10821011)

---

