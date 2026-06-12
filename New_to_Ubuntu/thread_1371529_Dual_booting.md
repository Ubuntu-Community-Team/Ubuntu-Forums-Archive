---
title: "Dual booting"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by kgonepostl on 2010-01-03
9.10 now uses grub2 I believe and I'm trying to backup my mbr but I'm having issues with the other tutorials that tell me to back up the menu.lst

I did a manual find on the entire hard drive and no menu.lst
How do I backup my mbr before dual booting windows xp onto my existing ubuntu 9.10?

---

### Post by Mahngiel on 2010-01-03
you won't need your master boot record from windows after you install ubuntu. in fact, the next time you upgrade/update, it'll ask you to autoremove 'mbr'. don't worry, grub2 will take care of you forever.

---

### Post by audiomick on 2010-01-03
> **kgonepostl said:**
> 9.10 now uses grub2
Yes it does, if it was a fresh install. If it was upgraded from a previous version, it will still have the old grub. If you can't find menu.lst anywhere, you have Grub2. (Assuming you really haven't overlooked something)


> How do I backup my mbr before dual booting windows xp onto my existing ubuntu 9.10?
I take it you want to add an XP install to a computer which currently has only Ubuntu on it.
Have a look here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by SecretCode on 2010-01-03
Simple way: 
```
sudo dd if=/dev/sda of=~/backupmbr bs=1 count=512
```
But be careful with the dd command; a typo could wipe out your whole drive.

Do you just have Ubuntu on the system now, and you're adding XP? Do you have a partition set up for it already? Do not let XP change your partitioning!

---

### Post by kgonepostl on 2010-01-03
I'm going to shorten the ubuntu partition, install xp on the partition and have grub take care of it.

This is my parents computer and I'm an uber n00b to linux. They have a really old p4 and 768 megs ram. I figured linux would be great for them. I changed the swappiness to 10 and the things running great. However, I think it would be convenient for them to boot into xp if they get too confused at times.

I'm going to become very familiar over the next year. I've been putting off way too long.
When I install xp onto the empty ntfs partition I create won't windows take over the mbr?

To clarify I don't have to back up the mbr?
Just to clarify again, this is a linux first and windows after dual boot. I believe that windows will overwrite with it's own mbr and after reading the tuturial they tell me to make a backup of my master boot record.

1.) I have 9.10 updated and it's fully allocating the drive
2.) gonna shrink it with gparted from the ubuntu live cd
3.) format the second partition with ntfs and install windows

I can handle the tutorial. I know that's not how it's done but I want to back up the mbr is all. I don't know why you have to if you can boot from a live cd. What's the point in backing up the mbr when adding xp to a existing ubuntu installation? Can somebody clarify?

---

### Post by SecretCode on 2010-01-03
Backing things up is always good. Don't question it. :)

Yes, XP will rewrite the MBR, and then you run grub-install and update-grub from Ubuntu to fix the bootloader.

The main reason why you backup the MBR is that it also contains the partition table, and if something happens to that it's not so simple to replace it.

---

### Post by Mark Phelps on 2010-01-03
> **kgonepostl said:**
> ... What's the point in backing up the mbr when adding xp to a existing ubuntu installation? Can somebody clarify?

Actually, with Ubuntu installed first, there is little point in backing up the MBR because it's a simple process to reinstall the MBR from an Ubuntu LiveCD.

---

### Post by kgonepostl on 2010-01-03
> **Mark Phelps said:**
> Actually, with Ubuntu installed first, there is little point in backing up the MBR because it's a simple process to reinstall the MBR from an Ubuntu LiveCD.

sudo  grub-install
sudo grub-update

? That simple? Seems about right, seems too easy.....

This is my parents computer. I gotta head back to my apartment in two hours and I don't wanna fuxor it. After windows takes over the bootloader I boot from the livecd and sudo grub-install and than sudo grub-update and that's it?

---

### Post by kgonepostl on 2010-01-03
*****bump

---

### Post by kansasnoob on 2010-01-03
This should fix you up if it's grub2:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

You can be certain what version of grub you have by going to terminal and running:

```
grub-install -v
```

1.97 is grub2, 0.97 is legacy grub

---

### Post by kgonepostl on 2010-01-04
Update: 

I installed xp and through the setup the screen goes blank. I don't even think it completes the installation of xp. I've been checking around and it seems I need to make the linux partitions inactive before I install xp.  

Btw, is there a way to accomplish this without running all these terminal lines? None of the commands make sense to me. DD? Sudo? It's all foreign to me at the moment. This is my first time using linux so if there's something graphical out there that will allow me to make my linux partitions inactive so I can properly install xp please let me know!

Right now I'm standing at a black screen apon boot FYI

---

### Post by kansasnoob on 2010-01-04
Did you leave the newly partitioned space unformatted? I've found that works better than preformatting to ntfs.

Look at pages 3 & 4 here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

Oh, and please tell me you're installing to a Primary partition. Windows won't play well in a logical partition.

---

### Post by SecretCode on 2010-01-04
> **kgonepostl said:**
> Btw, is there a way to accomplish this without running all these terminal lines? None of the commands make sense to me. DD? Sudo? It's all foreign to me at the moment. This is my first time using linux so if there's something graphical out there ...

The command line is good! Embrace it! :) I'm only half joking - you can get by in Ubuntu perfectly well without a command line, but dual booting - at least when you need to resize partitions - requires a bit more care.

(Consider downloading clonezilla live CD and using that to back up your disk. It has a lot of text-mode prompts, but you don't have to type any command lines! However, this is not going to help you with your windows installation.)

> **kgonepostl said:**
> ... to make my linux partitions inactive so I can properly install xp please let me know!

Hmm. This is the first I've heard of having to make linux partitions inactive. But nothing surprises me with XP? Do you not get the prompt during XP installation, shown on page 4 of the article kansasnoob linked?

---

### Post by kgonepostl on 2010-01-04
> **SecretCode said:**
> The command line is good! Embrace it! :) I'm only half joking - you can get by in Ubuntu perfectly well without a command line, but dual booting - at least when you need to resize partitions - requires a bit more care.

(Consider downloading clonezilla live CD and using that to back up your disk. It has a lot of text-mode prompts, but you don't have to type any command lines! However, this is not going to help you with your windows installation.)



Hmm. This is the first I've heard of having to make linux partitions inactive. But nothing surprises me with XP? Do you not get the prompt during XP installation, shown on page 4 of the article kansasnoob linked?


Ya................it doesn't even pop up that dialog. I freakin wish it would
Primary hard drive or primary partition? What do you want me to do? I just followed this guide step by step

---

### Post by SecretCode on 2010-01-04
OK ... might need you to go to the command line again! ...

Boot the ubuntu live cd, open Applications > Accessories > Terminal, and type
```
sudo fdisk -l
```
If you can get online with firefox paste the output here.

---

### Post by kgonepostl on 2010-01-04
> **SecretCode said:**
> OK ... might need you to go to the command line again! ...

Boot the ubuntu live cd, open Applications > Accessories > Terminal, and type
```
sudo fdisk -l
```If you can get online with firefox paste the output here.

Here ya go

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13058   104888353+  83  Linux
/dev/sda2   *       13059       25806   102398310    7  HPFS/NTFS
/dev/sda3           38635       38913     2241067+   5  Extended
/dev/sda5           38635       38913     2241036   82  Linux swap / Solaris

---

### Post by Methuselah on 2010-01-04
I think windows has some restriction as to what type of partition it is installed to but I don't quite remember the details.

---

### Post by kgonepostl on 2010-01-04
> **Methuselah said:**
> I think windows has some restriction as to what type of partition it is installed to but I don't quite remember the details.

Ya, I'm in the same boat. I remember dual booting before, I remember windows being picky, just forgot what kinda picky it was......:lolflag:

Well that's my list, right now I'm just sitting at a blank screen after the windows loading screen.  I'm just spooked is all, I don't know if there's anything wrong but I thought when you installed windows your computer would allow you to start up windows right?

I don't know much but I got the faintest idea that after the loading screen it can't locate the partition that windows is on so it goes blank?

That's just my thoughts . Thought i'd throw out my ideas before I head to sleep.
If you guys know what the issue is and how to fix it please let me know! Hope to have some sort of solution soon

---

### Post by Methuselah on 2010-01-04
Is the partition windows installed to a primary partition?
I think it has to be; it won't work correctly from an extended/logical partition.

---

### Post by SecretCode on 2010-01-04
Well ... nothing wrong there that I can see. The partition available for Windows is a primary partition.

I found this: [Installing Windows XP on existing Linux « Online Universe](http://onlineuniverse.wordpress.com/2008/05/01/installing-windowsxp-on-linux/) which explains how to hide/inactivate the linux partitions ... but it's solid wall-to-wall command line and hex editing. I don't think you'll be comfortable with it. 

But I also suspect there may be something else wrong. When you try the XP install do you at least get the blue text screen "Windows Setup"? And how far does it get? Exactly what "loading" screen do you get?

---

### Post by Methuselah on 2010-01-04
Oh, yeah he did post fidsk -l and it looks fine so the partition shouldn't be an issue.
I wonder if he has RAID enabled in the Bios?
Windows will usually need drivers on install.

---

### Post by kansasnoob on 2010-01-04
Well, I think this looks OK:

> Device Boot Start End Blocks Id System
/dev/sda1 1 13058 104888353+ 83 Linux
/dev/sda2 * 13059 25806 102398310 7 HPFS/NTFS
/dev/sda3 38635 38913 2241067+ 5 Extended
/dev/sda5 38635 38913 2241036 82 Linux swap / Solaris

You can get a more "human readable" output by going to terminal in Ubuntu and:

```
sudo parted /dev/sda print
```

Just as an example:

```
Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  76.4GB  36.9GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  100GB   15.7GB  logical   ext3
13      100GB   107GB   6835MB  logical   ext3
14      107GB   122GB   15.1GB  logical   ext3
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3

```

But I see that your sda2 already shows ntfs and you said:

> 1.) I have 9.10 updated and it's fully allocating the drive
2.) gonna shrink it with gparted from the ubuntu live cd
**3.) format the second partition with ntfs and install windows**

Whereas I said, "Did you leave the newly partitioned space unformatted? I've found that works better than preformatting to ntfs."

Unformatted means select no file system, just leave the new "free space" greyed out like this:

[ATTACH]142415[/ATTACH]

Note: I realize that doesn't show the extended and logical partitions that contain swap!

Anyway boot into Ubuntu and go to Terminal and run:

```
sudo parted /dev/sda print
```

If sda2 shows "primary" in the Type column then install gparted if you haven't already (**if it does not show primary STOP and post the full output here!**):

```
sudo apt-get install gparted
```

If it prompts like "gparted already newest version so not installed" that's OK, just close the Terminal and go to System > Administration > Gparted.

In Gparted right click on sda2 (the ntfs partition) and select Delete, then click on the green "Apply" check mark.

When that's done just close Gparted, etc, insert the Win XP install disc and reboot! I bet then you'll get to this screen:

[ATTACH]142414[/ATTACH]

Just select "Unpartitioned Space" and I'll bet you can complete the installation.

---

### Post by kgonepostl on 2010-01-04
> **kansasnoob said:**
> Well, I think this looks OK:



You can get a more "human readable" output by going to terminal in Ubuntu and:

```
sudo parted /dev/sda print
```Just as an example:

```
Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  76.4GB  36.9GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  100GB   15.7GB  logical   ext3
13      100GB   107GB   6835MB  logical   ext3
14      107GB   122GB   15.1GB  logical   ext3
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3

```But I see that your sda2 already shows ntfs and you said:



Whereas I said, "Did you leave the newly partitioned space unformatted? I've found that works better than preformatting to ntfs."

Unformatted means select no file system, just leave the new "free space" greyed out like this:

[ATTACH]142415[/ATTACH]

Note: I realize that doesn't show the extended and logical partitions that contain swap!

Anyway boot into Ubuntu and go to Terminal and run:

```
sudo parted /dev/sda print
```If sda2 shows "primary" in the Type column then install gparted if you haven't already (**if it does not show primary STOP and post the full output here!**):

```
sudo apt-get install gparted
```If it prompts like "gparted already newest version so not installed" that's OK, just close the Terminal and go to System > Administration > Gparted.

In Gparted right click on sda2 (the ntfs partition) and select Delete, then click on the green "Apply" check mark.

When that's done just close Gparted, etc, insert the Win XP install disc and reboot! I bet then you'll get to this screen:

[ATTACH]142414[/ATTACH]

Just select "Unpartitioned Space" and I'll bet you can complete the installation.

Yup, thanks for your help but I did take your advice last night and used gparted to turn it into unformatted space, than I formatted using ntfs full, still nothin

---

### Post by kansasnoob on 2010-01-04
Think again:

> Yup, thanks for your help but I did take your advice last night and used gparted to turn it into unformatted space, **[COLOR="Red"]than I formatted using ntfs full[/COLOR]**, still nothin

I've told you twice now, leave the new blank space unformatted. **Do NOT format it to ntfs!**

If you look at pages 3 & 4 of that tutorial that's exactly what they are doing:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

If you look at the first screenshot on page #4, which I also posted here, you have to select "Unpartitioned Space".

How can the Windows installer find unpartitioned space if you've already created a ntfs partition using Gparted?????????

---

### Post by kgonepostl on 2010-01-04
> **kansasnoob said:**
> Think again:



I've told you twice now, leave the new blank space unformatted. **Do NOT format it to ntfs!**

If you look at pages 3 & 4 of that tutorial that's exactly what they are doing:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

If you look at the first screenshot on page #4, which I also posted here, you have to select "Unpartitioned Space".

How can the Windows installer find unpartitioned space if you've already created a ntfs partition using Gparted?????????

Sorry, I said I left it unformatted and let windows turn it into ntfs using the full option during the installation precedure on the partition windows was being installed to.

To reiterate, I turned the partition unformatted using linux live, booted up xp, and used the ntfs full option.:)

Here's something weird, I'm in linux live right now and I can't simply 
sudo grub

---

### Post by kansasnoob on 2010-01-04
> Here's something weird, I'm in linux live right now and I can't simply
sudo grub

Because "sudo grub" is deprecated with grub2! That's why I posted this link:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

---

### Post by SecretCode on 2010-01-04
> **SecretCode said:**
> But I also suspect there may be something else wrong. When you try the XP install do you at least get the blue text screen "Windows Setup"? **And how far does it get? Exactly what "loading" screen do you get?**

```
sudo answer this question
```

:P

---

### Post by kgonepostl on 2010-01-04
> **SecretCode said:**
> ```
sudo answer this question
```:P

I believe all the way. It always takes so damn long to install xp so I remeber seeing 9 minutes left on my last install than I went back to rockin my other computer. I didn't see it finish but I assume it did because the computer restarted

I'm following the grub2 guide right now btw. Maybe if I can restore grub it'll just let me in. Who cares if xp comes to a blank screen. 

I'm gonna restore grub and if nothing works I'll install xp first and ubuntu after. SEEMS-WAY-EASIER-THAT-WAY:lolflag:

---

### Post by kansasnoob on 2010-01-04
Restoring grub2 should be as simple as:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then, to find Windows, the first time you boot into Ubuntu go to terminal and run:

```
sudo update-grub
```

And wait for it to say "done".

Note: if any of the above commands I tied together with <space&&space> fail then run the individual commands, ie:

sudo mount /dev/sda1 /mnt
sudo mount &#8211;bind /dev /mnt/dev
sudo mount &#8211;bind /proc /mnt/proc
sudo chroot /mnt

grub-install /dev/sda

exit

sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

