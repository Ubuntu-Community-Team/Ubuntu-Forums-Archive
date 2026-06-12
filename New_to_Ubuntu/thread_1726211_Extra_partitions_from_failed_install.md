---
title: "Extra partitions from failed install"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by John Swindle on 2011-04-10
How can I deal with extra partitions created in a failed attempt to install Ubuntu? 

I installed Ubuntu 10.10 to dual-boot on the main hard drive on a machine that already had Windows XP Media Center Edition version 2002 Service Pack 3.  The first try at installing Ubuntu hung and failed. The second succeeded. But I think I have a couple of left-over partitions--like 70 GB or so total--I don't know how to check--that neither XP nor Ubuntu recognize as available.

---

### Post by Dutch70 on 2011-04-10
Hi and welcome to UF

Open Gparted and take a screenshot of it, save it to your desktop & attach it to your next post using the paper clip in the toolbar.

---

### Post by akakingess on 2011-04-10
Could you give us just a little more information, such as the # of drives, size, etc. if you can get into Ubuntu run from the terminal the following:```
fdisk -l
``` and that is a lower case l. Post the output here so we have a better idea of what you are working with. Also, see what Gparted shows, it should be an available app, or just type gparted from with the terminal and again post that output.

---

### Post by John Swindle on 2011-04-10
I can see results from gparted, but how do I copy them to post them?

Here's what fdisk -l says:

Disk /dev/sda: 1500.3 GB, 1500301908992 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9728b1c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         564       10338    78512065+   7  HPFS/NTFS
/dev/sdb2               1         563     4522266    b  W95 FAT32
/dev/sdb3           10338       24322   112325633    5  Extended
/dev/sdb5           15000       23936    71781376   83  Linux
/dev/sdb6           23937       24322     3094528   82  Linux swap / Solaris
/dev/sdb7           10338       14803    35864576   83  Linux
/dev/sdb8           14803       15000     1579008   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Dutch70 on 2011-04-10
Take a screenshot of it, with the "Prt Scrn" or "Sys Rq" key on your keyboard. save it to your desktop and use the paper clip to "attach" it to your post.

---

### Post by John Swindle on 2011-04-10
I think I have attached a screenshot of gparted output for the internal hard drive.

---

### Post by Dutch70 on 2011-04-10
Okay, you're going to want to delete partitions sda5 & sda6 for starters. Go ahead and do that.

Right click them, select delete, then click the check mark to apply the changes.

After you do that, run the following command in a terminal...
```
sudo update-grub
```

Then you're going to have to boot up to the live cd/usb to get your space back.

---

### Post by John Swindle on 2011-04-10
I'm getting this kind of response:

Unable to delete /dev/sdb6!
Please unmount any logical partitions having a number higher than 6
OK

---

### Post by Dutch70 on 2011-04-10
Ok...go ahead and boot up to your live cd or usb stick & try it again.

What I suggest you do is to shrink your ubuntu partition that is now sdb7 down to about 15-20GB, and use the rest of your hdd for a /home partition. You'll have to recreate your swap partition to do that, but that's not much trouble at all & this will get you the best set up for long term.

---

### Post by John Swindle on 2011-04-10
I guess I could run Ubuntu from the removable USB stick to use gparted to delete hard drive partitions 5 through 8, and then try installing Ubuntu to the hard drive all over again. . . . .

---

### Post by oldfred on 2011-04-10
Gparted/liveCd's usually mount swap which is in your extended partition which is then preventing you from deleting the partitions. Click on swap and right click swap off (maybe on both swaps).

If you have not done much and want to start over that is fine. But I suggest you create partitions manually. There is some risk in deleting the windows partition if the wrong buttons are clicked.

Whatever make sure you have good backups.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Dutch70 on 2011-04-10
That's not a bad idea if you don't have anything to lose.

In that case, I would recommend creating your partitions first. 

"/" aka "root" 15-20Gb-this is where Ubuntu lives.

/home - similar to documents & settings in windows. This is not necessary, but is strongly recommended.

Swap - as I said, equal to or slightly larger than the size of your physical RAM, unless you have very little RAM.
[[COLOR="Red"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by John Swindle on 2011-04-10
Sorry--I confused myself when I answered my own message!

I understand booting up the USB stick and trying again. I understand shrinking sdb7 (with gparted, right?).

I do not understand /home partition.  I do not understand how to recreate the swap partition.

---

### Post by Dutch70 on 2011-04-10
Yes, you would shrink sdb7 with Gparted.

/home is where all your files & folders, including your settings are stored. So, if/when you have to re-install, you won't lose your data. 

To create a swap partition, you just right click the unallocated space, select "new" partition and format it to "swap". You will have to modify your fstab, but that's not too difficult.
oldfred is the man though. :D
He helped me with mine btw.

Reinstalling is probably easier if you're not losing anything.

---

### Post by John Swindle on 2011-04-10
oldfred, thank you! Lots of useful information. I'll print some of it out before I proceed. I'll move slowly--because I want to get it right, and because I have a cold, and because maybe I move slowly, and then I'll report back what works and mark the thread solved.

---

### Post by John Swindle on 2011-04-10
Duke70, thank you for all the good advice! I'll report back what works--may take me a day or two. John

---

### Post by Dutch70 on 2011-04-10
You're quite welcome, It's not a really big job at all. Especially if you decide to reinstall. 

Oldfred gave a lot of good useful information, but the links he gave that I think you'll find most useful are these 2.
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")
And this one will help with partitioning. You'll be surprised how easy it really "was" once you're finished...lol. 
[[COLOR="RoyalBlue"]http://members.iinet.net.au/~herman546/p22.html[/COLOR]]("http://members.iinet.net.au/~herman546/p22.html")

---

