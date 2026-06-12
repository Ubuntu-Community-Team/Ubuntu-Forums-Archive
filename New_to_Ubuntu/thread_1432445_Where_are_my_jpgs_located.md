---
title: "Where are my jpgs located"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by zunebuggy on 2010-03-17
I had Windows XP with Ubuntu as a dual boot. I have a Canon Rebel XTi Camera and one time I was checking out how well Ubuntu downloaded photos from my camera and downloaded some. Then my Windows XP became virus infected and wouldn't boot. I ended up making this dual boot hard drive a slave in another computer so I can get all my files off. I see all my files and photos saved by XP, but the photos I downloaded while in Ubuntu don't seem to be visible or available. Where would I find them or are they gone forever?
 
Thank you.
 
:guitar:

---

### Post by audiomick on 2010-03-17
Hallo.
you had best supply a bit more information.

Is the computer that the drive is now in also an Ubuntu system?
Can you see anything at all on the old drive in the Ubuntu partition(s)?
Do you remember where you put the photos on the Ubuntu partition ? i.e. in your user folder, in a folder inside that or whatever.

---

### Post by ubudog on 2010-03-17
Are they in your Pictures folder?

---

### Post by startrekker on 2010-03-17
If you can see the Ubuntu partition you might check under the home/yourusername/Pictures
or
home/yourusername/Photos if you use the default F-Spot (the picture manager program preinstalled on Ubuntu) they will probably be here and under a year month then day folder.

if you are familiar with the terminal try
find | grep jpg
or
find | grep JPG

---

### Post by zunebuggy on 2010-03-17
The computer I am using to view the contents of the hard drive with is running XP and I am not seeing the Ubuntu partition. I guess that's not good. :(

---

### Post by audiomick on 2010-03-17
xp can't read Linux file systems. I had a thing on my old laptop that allowed it. I will see if I can find a link to it.

Another option would be to boot the machine off the Ubuntu live CD and do your copying from there.

edit: here, I think I had this one
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

there is also this
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

---

### Post by zunebuggy on 2010-03-17
Yeah I was thinking I could put the Ubuntu disk in and chose the option to Try Ubuntu Without Installing and see if it would see the partition. I will give it a try. Thank you very much. :p

---

### Post by vincentertainment on 2010-03-17
You're on the right track with the live cd. 
Have you tried gimp, F-spot, or any of the other photo programs under linux yet?

---

### Post by tommynz1975 on 2010-03-17
some one will correct me if  I am wrong.

If you download the super grub disk. possibly the  hiren boot disc will have it on.

and boot the system off this, it may find the installation of Ubuntu and boot it for you.

This Disc contains a bunch of utilities on it.

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)
on the left of the screen is a download link.

---

### Post by d3v1150m471c on 2010-03-17
Reasons why you pay attention to where you downloaded them to. Use the locate feature.

---

### Post by zunebuggy on 2010-03-20
This has gotten trickier... I have reconciled myself to the fact that I am not going to be able to get my photos. In Ubuntu, it can view the hard drive, but only the Windows XP partition and files. Yes, it weird but true. In XP, the drive does not show up at all. I want to go ahead and format this drive but I can't do this in XP if it will not recognize the drive and I tried to figure out how to format it in Ubuntu but do not know how. I did a search and it said something about FDISK and root, but I am so knew to Ubuntu that without examples I am not going to figure it out. I know I have to do it from Terminal. Can I do it from Demo Ubuntu? If so, if I format in Ubuntu, can I format it in FAT32 so I can put XP on it? I'd hate to lose this 120GB hard drive but right now it's a paperweight.
Thank you.

---

### Post by oldos2er on 2010-03-20
When you're booted from the LiveCD, can you run **sudo fdisk -l** in a terminal (Applications, Accessories, Terminal) and post the output here?

---

### Post by zunebuggy on 2010-03-20
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15241524

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xefabef60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15504   117210208+  82  Linux swap / Solaris

---

### Post by zunebuggy on 2010-03-20
Do you think I will be able to format the drive from LiveCD? 
 
Thank you

---

### Post by 3rdalbum on 2010-03-20
> **zunebuggy said:**
> This has gotten trickier... I have reconciled myself to the fact that I am not going to be able to get my photos. In Ubuntu, it can view the hard drive, but only the Windows XP partition and files. Yes, it weird but true.

Before doing anything else, why not ask around your local area and see if there are any people who know a little about Linux who can help you find your photos?

You still haven't told us how you transferred them to your system. Did you drag and drop them, or did you use F-Spot, or what?

> In XP, the drive does not show up at all.

No, it wouldn't. Windows only reads Windows partitions.

> I want to go ahead and format this drive... I know I have to do it from Terminal. Can I do it from Demo Ubuntu?

You don't have to do it from the terminal. The Ubuntu live CD contains a program called Gparted. Boot up the CD and go to Try Ubuntu. Gparted is under System > Administration > Partition Editor (it might be Gnome Partition Editor...).

This program will help you delete all partitions on the hard disk and reformat it, or just reformat a single partition depending on exactly what you want to do.

---

### Post by zunebuggy on 2010-03-20
Thank you. I did use F-Spot. I was trying it out to see how it compared to my Canon software in XP. I only tranferred one session of photos (maybe 30) and can't even remember what the photos were. Chances are, I left the photos on my CompacFlash card and re-transferred the same pics again to XP.  That's what I usually do and I end up with "tons" of duplicates that way. If I view the contents of the drive in Demo mode, I can see Windows XP files but not the Ubuntu files except for the demo user files and Photos for the demo user are empty. When I had my dual partition, I had a Username Joe and I logged in with my password. I do not know how to access and logged in as Joe from the demo mode.
 
Thanks,
Joe

---

### Post by zunebuggy on 2010-03-20
ubuntu@ubuntu:/media/Q$ dir
74f0d2274a4c5da1c93f5fc257  install           PHO32S
aaw7boot.log            IO.SYS           pics
ASLog.txt            isolinux           pool
ATI                LGSInst.Log        preseed
AUTOEXEC.BAT            md5sum.txt           Program\ Files
autorun.inf            MSDOS.SYS           README.diskdefines
boot.ini            MSOCache           RECYCLER
casper                My\ Installations  System\ Volume\ Information
Config.Msi            N360_BACKUP        temp
CONFIG.SYS            NTDETECT.COM       ubuntu
Diamond                ntldr           WINDOWS
dists                pagefile.sys       wubildr
Documents\ and\ Settings    PDOXUSRS.NET       wubildr.mbr
inferno.log            PENSOFT

Here is the root directory. The Hard Drive's name was Q (from Star Trek as I name all my shared drives as characters from ST). As you can see, all that is visible from demo ubuntu is the Windows folders.From /media/Q$ I was able to run the command find | greg jpg and it listed all jpgs from Windows XP.

---

### Post by 3rdalbum on 2010-03-21
I see... you've done an install using Wubi (the installer that runs in Windows). That's why you don't see an Ubuntu partition, because there isn't one.

Assuming that the item "ubuntu" in your Windows partition is a folder, then open it up and you should see a disk image in there. You can mount it from the Ubuntu live CD by double-clicking it (I'm hoping... I haven't tried that before).

If that doesn't work, the following commands should:

```
sudo mkdir /media/ubuntu
sudo chmod a+rw /media/ubuntu
sudo mount -o loop /media/Q/ubuntu /media/ubuntu
```

Then you should find your photos under /media/ubuntu/home/username/Pictures

I tend not to recommend using Wubi to install Ubuntu, because of several limitations, and because it becomes impossible to recover files from the Ubuntu side if your Windows partition goes belly-up.

---

### Post by zunebuggy on 2010-03-21
Before I saw this last post I tried the GParted suggestion above and I did Create Partition and chose the MSDOS option thinking I could then see it in Windows XP. Now I can't see it in XP or Ubuntu.  So I tried again with PC98 and got the same results. I don't think my data is deleted, because when I clicked Create partition it look about a second to finish. I just don't know how to get back to where I was from here. Or if I can. If I can get back to where I see the ubuntu directory then great.  Or if I can format it so XP recognises it, that's great too. I guess I jumped into Ubuntu with both feet :)

---

### Post by 3rdalbum on 2010-03-21
> **zunebuggy said:**
> Before I saw this last post I tried the GParted suggestion above and I did Create Partition and chose the MSDOS option thinking I could then see it in Windows XP. Now I can't see it in XP or Ubuntu.  So I tried again with PC98 and got the same results. I don't think my data is deleted, because when I clicked Create partition it look about a second to finish. I just don't know how to get back to where I was from here. Or if I can. If I can get back to where I see the ubuntu directory then great.  Or if I can format it so XP recognises it, that's great too. I guess I jumped into Ubuntu with both feet :)

You create a partition with an MS-DOS disk label, but then you need to actually format the partition. If you want Windows to be able to work with it, then you need to format it to fat32 or ntfs.

---

### Post by zunebuggy on 2010-03-21
I got it. I have my 120GB Hard Drive back in XP. Too bad I didn't try everything to recover the pictures, but im 99% certain that what was on there was duplicates of pics I already have and I didn't lose anything. Thank you everyone. :)

---

