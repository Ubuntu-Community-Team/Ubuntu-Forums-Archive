---
title: "Can't make casper-rw loop persistence file greater than 2.0 GB-Ubuntu 9.04"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-24
Hi!  When I put Intrepid on my flash drive, the biggest persistence file I could make was 4 GB, due to the FAT32 limitation.  However, with Jaunty, If I select a persistence file size larger than 2GB, the installer ends prematurely, and I end up with no casper-rw at all.  The flash drive is 8 GB.  Is there a way to remedy this?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-04-24
Bump

---

### Post by pi.boy.travis on 2009-04-24
I have tried this with a few different flash drives on a few different computers with a few different LiveCDs, but no avail.  I think a bug report needs to be files in usb-creator.

Any ideas?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-04-24
bump?

---

### Post by gittr_done on 2009-04-24
I used the 8.10 directions from Pendrive Linux for creating a persistent usb linux using windows.  
I changed all references in the bat files from 8.10 to 9.04.

It loaded to a 8GB TDK brand USB stick formatted to FAT32 and it accepted the 4GB casper-rw replacement.

This message is being provided through FF 3.0.9 under Uubuntu 9.04 on persistent usb.

Hope this helps, good luck.

gittr_done

---

### Post by pi.boy.travis on 2009-04-24
Normally, if the flash drive is more than 4GB, I'll use a persistence filesystem.  However, on this drive, I want to leave room for other files.

Is there any way I can do this with the usb-creator package?

Thanks for your reply!

---

### Post by pi.boy.travis on 2009-04-24
I'm stumped.  I have tested multiple USB drives on multiple machines with multiple disc images and LiveCDs.  The application returns no error.  It just works up until the "Making Persistence File", then it claims to be finished.  This worked perfectly in 8.10. . .

---

### Post by Myst3 on 2009-04-24
U have try this methode? [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/")

---

### Post by pi.boy.travis on 2009-04-24
I have just found the bug in Launchpad.  I am going to try to use one of the suggested workarounds and report back.

---

### Post by max.goedjen on 2009-04-25
OK, yeah, it's a limitation, I think it's been filed as a bug already (I updated one that was saying it wasn't persistent with the reason why). Here's what I've done for my (16GB) flash drive, which I almost like more. I make a two partition flash drive. The first partition is as large as I can make it minus 1.72GB (this is the size that the live portion of the flash drive + 1GB of persistence for settings, programs, etc), and make the 2nd partition 1.72GB. Basically, what this allows me to do is, when I plug my flash drive into a windows computer, as I often do for transferring files, the ~13GB drive mounts properly, and is isolated from the Ubuntu partition (windows can only see the first partition of a flash drive, and this actually kind of works well for us). When you're starting up the PC however, you can still boot to the flash drive, and (for me on a couple of dell machines, at least) it will boot to the 2nd partition, where you will have 1GB persistence as well as full access to the 1st(data) partition. (I haven't played around with it yet, but you could probably even set your account's home directory to be on the data segment, keeping all data there, and all settings/programs in the persistence area). Basically this allows you to have full access to your files anywhere, instead of them being contained in the persistence area.

NOTE: THIS (AS FAR AS I KNOW) ONLY WORKS WITH THE UBUNTU FLASH DRIVE CREATOR. (I KNOW you can't boot to the 2nd partition with the Fedora Live USB creator (regardless if you're putting Ubuntu/Fedora on the drive), and I can't confirm if this works with any other creators.

Max

---

### Post by pi.boy.travis on 2009-04-25
> **max.goedjen said:**
> OK, yeah, it's a limitation, I think it's been filed as a bug already (I updated one that was saying it wasn't persistent with the reason why). Here's what I've done for my (16GB) flash drive, which I almost like more. I make a two partition flash drive. The first partition is as large as I can make it minus 1.72GB (this is the size that the live portion of the flash drive + 1GB of persistence for settings, programs, etc), and make the 2nd partition 1.72GB. Basically, what this allows me to do is, when I plug my flash drive into a windows computer, as I often do for transferring files, the ~13GB drive mounts properly, and is isolated from the Ubuntu partition (windows can only see the first partition of a flash drive, and this actually kind of works well for us). When you're starting up the PC however, you can still boot to the flash drive, and (for me on a couple of dell machines, at least) it will boot to the 2nd partition, where you will have 1GB persistence as well as full access to the 1st(data) partition. (I haven't played around with it yet, but you could probably even set your account's home directory to be on the data segment, keeping all data there, and all settings/programs in the persistence area). Basically this allows you to have full access to your files anywhere, instead of them being contained in the persistence area.

NOTE: THIS (AS FAR AS I KNOW) ONLY WORKS WITH THE UBUNTU FLASH DRIVE CREATOR. (I KNOW you can't boot to the 2nd partition with the Fedora Live USB creator (regardless if you're putting Ubuntu/Fedora on the drive), and I can't confirm if this works with any other creators.

Max

That is a really fantastic idea!  I'll do that until a fix is released.  By the looks of the bug page, the install script that the builder uses just has to be tweaked.  Too bad I don't know Python. . .

---

### Post by max.goedjen on 2009-04-25
Yeah, it's been working really well for me, better than if I'd have been able to create a 15GB persistence file. It just works like a regular flash drive until you need to boot into it, and even then, easy access to all your files on both ends.

---

### Post by ljk on 2009-04-26
> **max.goedjen said:**
> OK, yeah, it's a limitation, I think it's been filed as a bug already (I updated one that was saying it wasn't persistent with the reason why). Here's what I've done for my (16GB) flash drive, which I almost like more. I make a two partition flash drive. The first partition is as large as I can make it minus 1.72GB (this is the size that the live portion of the flash drive + 1GB of persistence for settings, programs, etc), and make the 2nd partition 1.72GB. Basically, what this allows me to do is, when I plug my flash drive into a windows computer, as I often do for transferring files, the ~13GB drive mounts properly, and is isolated from the Ubuntu partition (windows can only see the first partition of a flash drive, and this actually kind of works well for us). When you're starting up the PC however, you can still boot to the flash drive, and (for me on a couple of dell machines, at least) it will boot to the 2nd partition, where you will have 1GB persistence as well as full access to the 1st(data) partition. (I haven't played around with it yet, but you could probably even set your account's home directory to be on the data segment, keeping all data there, and all settings/programs in the persistence area). Basically this allows you to have full access to your files anywhere, instead of them being contained in the persistence area.

NOTE: THIS (AS FAR AS I KNOW) ONLY WORKS WITH THE UBUNTU FLASH DRIVE CREATOR. (I KNOW you can't boot to the 2nd partition with the Fedora Live USB creator (regardless if you're putting Ubuntu/Fedora on the drive), and I can't confirm if this works with any other creators.

Max

Thanks for the advice. I'm not that concerned about using the USB flash drive for anything other than a portable Ubuntu system so I tried again but selected 1.9 GB as the size of the Documents & Settings section, without partioning the drive, but the result was catastrophic.

I'll try once more but I'll follow your workaround to the letter next time.

Thanks.

---

### Post by 67GTA on 2009-04-28
> **pi.boy.travis said:**
> I have just found the bug in Launchpad.  I am going to try to use one of the suggested workarounds and report back.

Can you give a link for the bug report? This is bugging me also. I wasn't thinking the other day, and tried to download a DVD image (4.2GB) to my Jaunty USB, and it stopped at 3.5GB. Then I remembered the fat32
limitation. It would be better to lets users choose their own filesystem instead of defaulting to fat32.

---

### Post by pi.boy.travis on 2009-04-28
> **67GTA said:**
> Can you give a link for the bug report? This is bugging me also. I wasn't thinking the other day, and tried to download a DVD image (4.2GB) to my Jaunty USB, and it stopped at 3.5GB. Then I remembered the fat32
limitation. It would be better to lets users choose their own filesystem instead of defaulting to fat32.

No problem.  There are a few of them, as there are several bugs that result in this behavior.


[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/352766](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/352766)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/352766](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/352766)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/352766](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/352766)

---

### Post by debernardis on 2009-05-02
> **max.goedjen said:**
> I make a two partition flash drive.

:guitar: Great, man! Simple and effective!

This is now the new setup for my Sandisk Extreme Cruzer Contour 16GB drive with Jaunty. It's a very quick stick,  advertised as 25MB/s reading, 18 MB/s writing.
I'll update the flash drives I've done for my friends, too. 

I have also a small (about 600 megs) partition on that stick, formatted as linux swap, for those MS Win-based host machines without one.

---

