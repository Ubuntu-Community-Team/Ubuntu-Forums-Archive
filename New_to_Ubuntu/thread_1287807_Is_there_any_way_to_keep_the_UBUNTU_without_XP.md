---
title: "Is there any way to keep the UBUNTU without XP?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Narendra on 2009-10-10
Hello,

I have installed UBUNTU on my computer with WUBI Installer in XP.

Now I want to get rid of XP and wish to have UBUNTU only on the computer. I think if I do that UBUNTU will also go.

Is there any way to keep the UBUNTU without XP?

Please advise.

---

### Post by orky7 on 2009-10-10
sorry....no way out

---

### Post by marshmallow1304 on 2009-10-10
Backup all your files (including hidden files in your /home), boot from the Ubuntu CD, install Ubuntu using the entire drive, then replace your files.

---

### Post by CaptainMark on 2009-10-10
just back up your files and do a fresh install with an ubuntu live disc

edit: damn too slow

---

### Post by Daniel1994 on 2009-10-10
wubi installs ubuntu "inside" xp, so there is no way to keep ubuntu but not xp.

I suggest backing up all your personal files in ubuntu on an external hard drive/USB/CD and then installing from the live CD.

Even slower.

---

### Post by ibuclaw on 2009-10-10
I may be mistaken, but I think you are all too slow ...

If you have already backed up all files you use on Windows, reboot into Ubuntu.
Insert an external hard drive, then open up **nautilus** and browse the directory:
```
/home
```
Right-click on your username directory, and you should see an option to **compress** it.
Name it what you want, then set the "**Location**" to where your external drive is mounted, then select "**Create**"
That will backup all Ubuntu files.

Next thing to do is reboot into the LiveCD, and startup the Installer.
When it asks, the easiest way is to "**Erase Entire Drive**" when asked how you would like to partition the disk for Ubuntu. But it is generally recommended that you have a separate /home partition though.

Once finished, just extract the backed up contents back into your home directory, and restore.

Regards
Iain

---

### Post by Narendra on 2009-10-12
Thank you very much for your replies.

I have 2 hard disks on my computer and The XP and The Ubuntu are installed separately on each drive, so if I wipe out XP, UBUNTU will be there, but how do I boot in the ubuntu?

If I need to fix Grub, the bootloader, please advise.

I am  too slow, had blod clot in the brain in 94 and now I am aged 60.

Regards.

---

### Post by MelDJ on 2009-10-12
you can try this: 
**How do I migrate to a real partition, and/or get rid of Windows entirely?**

 Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).  
As an alternative, the following script can be used with Wubi 8.04. 
Download [wubi-move-to-partition]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-move-to-partition") 
Open a terminal and run:  
sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10Replace /dev/sda9 with the partition where you would like to migrate the Wubi installation to, and /dev/sda10 with the appropriate swap partition (you can omit the second argument completely, in which case no swap will be setup). The two partitions must already exist and be empty (you can use any partitioning tool such as gparted to create them in advance). Note that the script will install grub as main bootloader replacing the existing bootloader, and it may not be easy to undo the changes (if things do not work as expected you will have to boot from a Live CD and replace/edit the bootloader manually). Also note that if you have multiple hard-disks, the disk order might have to be adjusted manually. 
 
[B]
[/B]



i copied it all from the wubiguide.. don't want to burden you to scroll down:)

---

### Post by philinux on 2009-10-12
> **tinivole said:**
> 
Right-click on your username directory, and you should see an option to **compress** it.
Name it what you want, then set the "**Location**" to where your external drive is mounted, then select "**Create**"
That will backup all Ubuntu files.



I tried this just for fun/test and I get a permission error :confused:.
```
An error occurred while adding files to the archive.

Permission denied

```

---

### Post by Paqman on 2009-10-12
+1 for LVPM.

In future, Wubi will be able to pull off this trick on it's own, I believe.

---

### Post by manoynmonic on 2009-10-12
Why not just install remastersys in your wubi install of Ubuntu, and use that to make a complete bootable dvd of your install including the home directory?  Burn it, then install off of that.  No downtime or nothin, all your apps will be there, all your files, everything.

---

### Post by MelDJ on 2009-10-12
> **manoynmonic said:**
> Why not just install remastersys in your wubi install of Ubuntu, and use that to make a complete bootable dvd of your install including the home directory?  Burn it, then install off of that.  No downtime or nothin, all your apps will be there, all your files, everything.

thats quite time consuming comparatively:)

---

### Post by Narendra on 2009-10-13
Thank you very much for your replies.

---

