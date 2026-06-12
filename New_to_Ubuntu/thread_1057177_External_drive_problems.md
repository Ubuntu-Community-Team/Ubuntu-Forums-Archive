---
title: "External drive problems"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by andjen on 2009-02-01
I've just got Vista to dual-boot with Ubuntu 8.04.

I've got an external hard drive with loads of info on it. I've just looked at this:

[http://ubuntuforums.org/showthread.php?t=1025651&highlight=external+hard+drive&page=4](http://ubuntuforums.org/showthread.php?t=1025651&highlight=external+hard+drive&page=4)

which is the last page of a 4-page thread. I too want to make the external drive available to both vista and ubuntu but surely there's another way besides re-formatting the disc??

Andjen

---

### Post by MarblePanther on 2009-02-01
What filesystem do you currently have on the external drive?

If it is FAT or NTFS, you will be fine. Ubuntu can read FAT and NTFS.

---

### Post by RIT_girl on 2009-02-01
I'm having external drive problem as well, I just bought the WD My Book and I want to set it up to automatically back up my computer..I guess this is the closest thread I found. 


PS, what is FAT and NTFS? I know they are filesystems, but what's the difference?

thanks :)

---

### Post by Crafty Kisses on 2009-02-01
> **RIT_girl said:**
> I'm having external drive problem as well, I just bought the WD My Book and I want to set it up to automatically back up my computer..I guess this is the closest thread I found. 


PS, what is FAT and NTFS? I know they are filesystems, but what's the difference?

thanks :)

Please read these: [http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table) and [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS).

---

### Post by MarblePanther on 2009-02-01
> **RIT_girl said:**
> I'm having external drive problem as well, I just bought the WD My Book and I want to set it up to automatically back up my computer..I guess this is the closest thread I found. 


PS, what is FAT and NTFS? I know they are filesystems, but what's the difference?

thanks :)



FAT and NTFS are the common filesystems used by windows.

---

### Post by andjen on 2009-02-01
It seems that a few people are problems with external drives.

Mine is a 500GB Lacie drive which is FAT formatted.

When I first boot into Ubuntu then the drive is shown in Places although it doesn't auto-mount. Once I've mounted it then it appears on the desktop (is that the word in Ubuntu?) although it soon loses the connection or no longer sees the drive because it disappears from Places and is no longer available.

The drive works fine in Vista so really I've got two questions:

1) Is there a way to auto-mount the drive when Ubuntu starts;
2) More importantly is there a way to keep the drive available?

Andjen

---

### Post by Crafty Kisses on 2009-02-01
While the external HD is plugged in, run the following command:
```
sudo fdisk -l
```
Please post the results back here.

---

### Post by MarblePanther on 2009-02-01
> **Codename said:**
> While the external HD is plugged in, run the following command:
```
sudo fdisk -l
```
Please post the results back here.

For clarification: run the command with the application called Terminal in Applications,Accessories, Terminal

---

### Post by andjen on 2009-02-01
Thanks for the prompt replies guys.

The output from 'sudo fdisk -l' is as follows:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe474ac88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13919   111795898+   7  HPFS/NTFS
/dev/sda2           13920       60801   376579665    5  Extended
/dev/sda5           13920       59577   366747853+  83  Linux
/dev/sda6           59578       60801     9831748+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)

Hope this is useful to you because it's not clear to me!!

Andjen

EDIT : Just to let you know that I booted into Ubuntu just prior to using the above 'sudo fdisk -l' command. I had to mount the external drive at that time but its now disappeared again so it was working for about 10 minutes (if that). The length of time that it works for seems to vary but I can't find a common reason why it just disappears!

---

### Post by Kaybar on 2009-02-01
:( Need help! Beginner needs to learn how to add a program, mount a separate hard drive, and emulate windows programs. (I don't know enough to know what else I need!)

---

### Post by SunnyRabbiera on 2009-02-01
> **Kaybar said:**
> :( Need help! Beginner needs to learn how to add a program, mount a separate hard drive, and emulate windows programs. (I don't know enough to know what else I need!)

Please dont take over someone e4lses topic, please make your own by clicking the new topic button at the top of the page

---

### Post by GMachine_24 on 2009-02-01
Just FYI

FAT32 - Is the file system for Windows 98, 95 and it stands for File Allocation Table

NTFS - Stands for New Technology File System (yeah, I know, hokey) and is the basis for Windows NT, 2000, XP and Vista.

I will let the others address what you have to do to make the Windows hard drive read/writable with your Ubuntu box. It's not that hard, but it takes some configuring.

Good luck.

---

### Post by valantis on 2009-02-01
hi it is not ntfs or some think like that your problem, 
just look two thinks. 
1 ) if you have some one program that make a library (mp3 library windows media player etc.) 
when someone program  like Microsoft media player library or sharing library with media player make your hdd to seems lock, Linux did not mount because see that another application use your drive. If you make force mount can see drive but maybe you loss data. 
2) make safe remove from vista , if says that your device is used from another application and can't safe remove now , think which program use files from you external hdd. 
your ubuntu works fine in any case .

---

### Post by Kaybar on 2009-02-01
> **Codename said:**
> While the external HD is plugged in, run the following command:
```
sudo fdisk -l
```
Please post the results back here.

Sounds good but---where how do do I find a command line on which to write the "sudo fdisk-l[/code]"

Thematerialon the disk is one of my backup copies.  Oh-I'm in Wisconsin, CST.:(

Thanks for any further information you can provide. I do love the Ubuntu design and would hate to go back to Windows!

---

### Post by absbegstarting on 2009-02-01
no,no,no

---

### Post by andjen on 2009-02-02
Hi

Just got up (I'm in England) and I see that there have been a few posts but mainly replies to other people's questions and not to my original one's.

Essentially, is there any way to make my external drive readable from both Vista and Ubuntu and, less importantly, can I make it auto-mount when Ubuntu starts?

Off to work now see you later.

---

### Post by MarblePanther on 2009-02-02
You havent been specific,  and i thought i already answered you.  If your harddrive is formatted with FAT or NTFS it will be readable in vista and in ubuntu.  Is this a backup drive?

If it doesn't appear on your ubuntu desktop, go back to vista and make sure you Safely Remove it.  If you dont properly eject it in vista it wont load in ubuntu.

---

### Post by andjen on 2009-02-02
Sorry MarblePanther, I obviously misinterpreted what you said earlier.

Thanks for all your help.

---

### Post by MarblePanther on 2009-02-02
I dont mean to appear stern or anything.  Sorry about that.
Is your hdd working in Ubuntu?

---

### Post by andjen on 2009-02-03
Yes thanks I've got it working now - as you said I just need to 'Safely Remove' in Vista before I boot into Ubuntu.

All I need to do now is to get my graphics card working properly coz the display keeps blanking on me but there's plenty of documentation on this subject already so please consider this thread closed.

Again, thanks for your help everybody.

---

