---
title: "[SOLVED] Need to set up for XP but cant!"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Aussieartist on 2008-12-22
Hi all, 
I need to set up my HP dv5t for XP (as it is required at work,) unfortunately when I installed 8.10 I think I killed the windows partition, as a result there is no NTFS partition for XP to install to.

I have the Ubuntu 8.10 disk, but it won't allow me to make an NTFS partition (only FAT), booting from XP disk will load drivers etc but crash when attempting to load Window$, I know both disks work. 

Assuming I have done something stupid...  how do I make it better? Can I install XP partition after Ubuntu? or do I need a partition format app or something? I don't mind starting everything from scratch, my files are backed up, just not my OSs.

Any advice greatly appreciated, (with novice instructions if possible!)
Aussie

---

### Post by laurielegit on 2008-12-22
Well if you want to make a NTFS partition I recomend you use GParted. It is availible as a app inside Ubuntu and also as a live cd. You can get it here: gparted.sourceforge.net or through the ubuntu repositaries. It will let you make one of your ubuntu partitions smaller and you can use the space created to install windows.

Best of luck,

Laurie

---

### Post by cozmicharlie on 2008-12-22
> **Aussieartist said:**
> Hi all, 
I need to set up my HP dv5t for XP (as it is required at work,) unfortunately when I installed 8.10 I think I killed the windows partition, as a result there is no NTFS partition for XP to install to.

I have the Ubuntu 8.10 disk, but it won't allow me to make an NTFS partition (only FAT), booting from XP disk will load drivers etc but crash when attempting to load Window$, I know both disks work. 

Assuming I have done something stupid...  how do I make it better? Can I install XP partition after Ubuntu? or do I need a partition format app or something? I don't mind starting everything from scratch, my files are backed up, just not my OSs.

Any advice greatly appreciated, (with novice instructions if possible!)
Aussie

Another option is to set up XP in Virtual Box.  I, like you, need XP for work so I have it installed via Virtual Box using Ubuntu as the host.    Install the virtualbox add-ons for seamless integration and you have a full working copy of xp right in Ubuntu.  This tutorial will show you how [http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/](http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/)  

Alternatively,
You did not mention if you plan to dual boot or not.  If so you could install XP (do a full install) then install Ubuntu and during installation it will set up everything for a dual boot.

---

### Post by Duck2006 on 2008-12-22
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Aussieartist on 2008-12-22
Thanks for the info. I'd rather have dual boot. At this point I want my Ubuntu for learning more about Linux (remember I've been using the OS for a grand total of a week now!) But I still need my safety net of XP for work and all of the old things I know.

Ideally I'd like to turn the thing on and choose XP for work and Ubuntu for home.

Looks like I did wipe my whole HD last night so I'm installing Ubuntu right now... 96% Linux and 3% swap.
I'll then try the GParted and see how I go...

This is a steep learning curve, but nothing ventured etc...
Thanks
Aussie

---

### Post by cozmicharlie on 2008-12-22
It probably would have been easier to install XP first then Ubuntu. Ubuntu detects your xp, creates new partitions and sets up the boot loader (Grub) for easy dual booting during the install process so it is real easy to set up.  You can still get it to work though - just a little more work.

---

### Post by Aussieartist on 2008-12-22
I suspect my XP iso cd is not working properly... I've done the partition with Gparted but when I boot from XP CD it still crashes... It's almost like it needs some previous evidence of a Window$ system in order to run... it's odd... I know this CD works fine when wanting to re-install XP... 

AND I'm all out of coffee!!!
Aussie

---

### Post by Duck2006 on 2008-12-22
Try doing a fix the mbr from the recovery mode

Boot the xp cd
press r to go into recovery
at the promp type fixmbr
quit or exit not sure been that long.

reboot the xp cd and do the install again.

---

### Post by Elfy on 2008-12-22
It's not installed yet:)

It might need to have the ntfs at the beginning of the drive or even empty space at the front. Not sure where you have put the partition for it.

---

### Post by Duck2006 on 2008-12-22
> **forestpixie said:**
> It's not installed yet:)

It might need to have the ntfs at the beginning of the drive or even empty space at the front. Not sure where you have put the partition for it.

No you can have the ntfs partition in the second partition or ect, Just make sure it is on the first hard drive.

---

### Post by kansasnoob on 2008-12-22
Assuming at this point you can still boot Ubuntu (not from live CD) post the output of:

```
sudo fdisk -l
```

That's a lower case L.

Or better yet post a screen-shot of Gparted.

---

### Post by kansasnoob on 2008-12-22
> **Aussieartist said:**
> I suspect my XP iso cd is not working properly... I've done the partition with Gparted but when I boot from XP CD it still crashes... It's almost like it needs some previous evidence of a Window$ system in order to run... it's odd... I know this CD works fine when wanting to re-install XP... 

AND I'm all out of coffee!!!
Aussie

Is it possible that it's an "upgrade" disc rather than a full install disc? If so maybe you can come up with an old 98 or ME disc.

Or I've had system specific discs fail due to hardware changes. That's typical of Win!

---

### Post by Aussieartist on 2008-12-22
I truely appreciate everyones help, makes me know I'm right in joining the Ubuntu family:)... If you could indulge me a bit further, here's what's happening:

When I boot from the XP cd it goes to a (blue) Windows Setup screen... not a typical XP setup screen. There isn't a recovery mode, or a command prompt. It says loading (mentions all kinds of device drivers) then screen says: 

*"A probllem has been detected and Windows has been shut down to prevent damage to your computer. If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps: Check for viruses on your computer. remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK/F to check for hard drive corruption, and then restart your computer. Technical information: ***STOP: 0x0000007b (0xF78D2524, 0xc0000034, 0x00000000, ox00000000)"*

Still no coffee, now drinking my wife's tea!!!
Aussie:(

---

### Post by Aussieartist on 2008-12-22
I'm doing this discussion on another computer... I'll do the fdisk on the ubuntu machine and type it here - standby

---

### Post by Aussieartist on 2008-12-22
Kansasnoob asked for this info:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34c662a0

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1           37698       38913     9767520    5  Extended
/dev/sda2   *           1       12138    97498453+  83  Linux
/dev/sda5           37699       38913     9759487+  82  Linux swap / Solaris

Partition table entries are not in disk order

Thanks
Aussie

---

### Post by kansasnoob on 2008-12-22
> **Aussieartist said:**
> Kansasnoob asked for this info:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34c662a0

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1           37698       38913     9767520    5  Extended
/dev/sda2   *           1       12138    97498453+  83  Linux
/dev/sda5           37699       38913     9759487+  82  Linux swap / Solaris

Partition table entries are not in disk order

Thanks
Aussie

I see no reason why the previously posted:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Should not work other than a problem with the XP disc.

As I mentioned before that could be because it's an upgrade disc, in which case you need to install Win 98 or ME first (generally easy if you have discs), or if it's a system specific disc that does not like the current hardware.

If it's a full install Win XP disc I'd call XP support after buying coffee! Just be sure and play dumb ............ like, "My computer crashed so I decided to try a reinstall"! No mention of Ubuntu or Linux!

---

### Post by hexanol on 2008-12-22
This is the first time I hear of something like this, and I have done numerous XP install...

This is an [article]("http://support.microsoft.com/kb/324103/en-us") about what Microsoft has to say about "STOP 0x0000007B". But I guess it won't help you.

Your output of fdisk looks a bit weird, it's not sure to understand why there's such a hole between your /dev/sda2 (block 1-12138 ) and /dev/sda1 (block 37698-38913). But this might be due to my incomplete knowledge.

---

### Post by arpanaut on 2008-12-22
Not sure here, but since the whole disk is partitioned as an "extended" this may be the issue.
AFAIK windows is looking for a "primary" partition to install to...

Also with some types of disks, before windows will install some special drivers need to be installed... It's been a long time since I have installed windows so my memory of the details of this is foggy (oldtimers disease).

anyway my 2 cents... Hope it helps!

---

### Post by LowSky on 2008-12-22
You could always creat a Fat32 Partiton with gparted, and then when you go to install WinXP you can change it to NTFS from there.
I've done that a few times after buying hard drives and only having a LiveCD around

---

### Post by kansasnoob on 2008-12-22
> **hexanol said:**
> This is the first time I hear of something like this, and I have done numerous XP install...

This is an [article]("http://support.microsoft.com/kb/324103/en-us") about what Microsoft has to say about "STOP 0x0000007B". But I guess it won't help you.

Your output of fdisk looks a bit weird, it's not sure to understand why there's such a hole between your /dev/sda2 (block 1-12138 ) and /dev/sda1 (block 37698-38913). But this might be due to my incomplete knowledge.

So, you've found XP upgrade discs to just "install" XP with no prior Win system?

You've never had a Win reinstall fail after upgrading hardware?

I must just have bad luck!

---

### Post by Aussieartist on 2008-12-25
Thank you to everyone for your help. I ended up putting on Virtual Box and running XP within. Looks like my XP CD was good... at least when installing on a formatted virtual drive.

Cheers
Aussie:P

---

### Post by anewguy on 2008-12-25
Glad you got things working - a previous poster was correct in this case.  You needed to make the partition you intended to install Windows in a primary partition - you could have done so with gparted. If this the disk is already partitioned, Windows expects to find an available primary partition to install to. I also am curious about the seemingly empty space on your drive that doesn't show in the list.  It should at least say free space, unallocated or some such thing.  In addition, if you ever decide you want to try dual boot again, follow the previous mentioned advice - delete the partitions from your disk, make a primary partition for Windows of the size you want, install Windows, THEN install Linux.  You'll eliminate some extra work to get everything to boot if you do!

Good luck!  Hope you enjoy Ubuntu!

Dave :)

---

