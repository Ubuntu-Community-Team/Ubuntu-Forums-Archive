---
title: "Windows 7 Installer Partition Error?"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2011-07-03
It kills my insides to post this, as I have been using Ubuntu 11.04 as my sole OS now for about 8 months but the need has come to add Windows 7 to my system.

Reason being is that I need to use Illustrator CS5 & Photoshop CS5 for some editing work at a magazine.

GIMP can only do so much and Scribus just hasn't the features Illustrator has. I have tried Wine and neither have worked for me :(

Basically when I pop my Win 7 DVD in the drive, it boots into the installer but when I go to setting the partitions that I want Windows to use I get the error:

```

Setup was unable to create a new partition or locate an existing system partition. See the setup log files for more information

```

I have 4 hard drives in the system. 2 x 1TB WD SATA2 Drives (Storage), 1 x 120GB SSD Drive (Linux System) and 1 x 750GB WD SATA2 Drive (Hopefully for Windows 7).

Now I have used gparted and formatted the 750GB as an ntfs partition, this didn't work. I have also split the drive with half ntfs and half unallocated, again no go. Every time I get the above error?

Anyone had or heard of this issue before?

---

### Post by grahammechanical on 2011-07-03
I am not an expert on this subject but as no one else has answered may I say, that as you are installing Windows to its own hard disc, that you remove the other discs and let the Windows installer treat the 750GB drive as a blank drive that needs formatting.

May be you need to use Windows Utilities to format and partition for the installer to recognize what it is looking at.

Regards.

---

### Post by oldfred on 2011-07-03
When you partitioned was it a primary partition? With one or two NTFS partitions it should be. But did you also put a boot flag on the partition. That is the active partition in windows that it knows to boot from, install to, or repair if needed.

---

### Post by wildmanne39 on 2011-07-04
> **terrykiwi83 said:**
> It kills my insides to post this, as I have been using Ubuntu 11.04 as my sole OS now for about 8 months but the need has come to add Windows 7 to my system.

Reason being is that I need to use Illustrator CS5 & Photoshop CS5 for some editing work at a magazine.

GIMP can only do so much and Scribus just hasn't the features Illustrator has. I have tried Wine and neither have worked for me :(

Basically when I pop my Win 7 DVD in the drive, it boots into the installer but when I go to setting the partitions that I want Windows to use I get the error:

```

Setup was unable to create a new partition or locate an existing system partition. See the setup log files for more information

```

I have 4 hard drives in the system. 2 x 1TB WD SATA2 Drives (Storage), 1 x 120GB SSD Drive (Linux System) and 1 x 750GB WD SATA2 Drive (Hopefully for Windows 7).

Now I have used gparted and formatted the 750GB as an ntfs partition, this didn't work. I have also split the drive with half ntfs and half unallocated, again no go. Every time I get the above error?

Anyone had or heard of this issue before?Hi, also did you try windows in virtualbox it runs great in virtualbox, the only thing that does not work well is games.

---

