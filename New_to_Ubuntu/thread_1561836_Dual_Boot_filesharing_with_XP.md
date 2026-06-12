---
title: "Dual Boot filesharing with XP"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by ChemShock on 2010-08-26
What I want to do is set up a way to share files between the partitions of Lucid and XP. Idealistically, there is a folder on both sides of the partition and it is a "drag and drop" method of sharing. Then switch over to the other and it appears and be usable. From my understanding, Samba is more for sharing between multiple computers on a network. I just want it set up to share on this computer itself. Any ideas? Much appreciated in advanced.

---

### Post by TwoEars on 2010-08-26
First things first, you will need a compatible filesystem between the two. For this, I recommend the current default one for Windows, ntfs. The best method you will have is to use the files in a folder, for example ```
C:\Shared Files
``` on Windows, then access those files in there directly from Windows, and then from Linux too. Files saved on the Linux filesystems cannot be easily accessed, if at all, from Windows, so your best bet is to do it the mentioned way.

---

### Post by ChemShock on 2010-08-26
What I used to do was on ubuntu, I created a shortcut folder that linked to my windows desktop folder which created a one way tunnel to XP. So, from my understanding, if I share my "Shared Folders" on XP and create my shortcut folder on my ubuntu partition to link with my shared folders, will that resolve the issue?

---

### Post by rportnoy on 2010-08-26
> **ChemShock said:**
> What I want to do is set up a way to share files between the partitions of Lucid and XP. Idealistically, there is a folder on both sides of the partition and it is a "drag and drop" method of sharing. Then switch over to the other and it appears and be usable. From my understanding, Samba is more for sharing between multiple computers on a network. I just want it set up to share on this computer itself. Any ideas? Much appreciated in advanced.
Yes, linux partition cannot be read from windows without using 3rd party software. like [http://www.fs-driver.org/](http://www.fs-driver.org/) 
Many linux distro automaticaly detect and put the command in fstab if it's not, you must set it manually
/dev/hda for first hdd /dev/hdb for second etc..

/dev/hda1 first partition hda2 second etc...

Assuming you have only 1 hdd:

hda1 usually the primary C: , and hda2 also primary but maybe extended dos partition depend on your partition table. and hda3 D:, hda4 E: etc.

But if you have more than 1 hdd it will different

for fstab format understanding please go here [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by ChemShock on 2010-08-26
Oh, ok I get it now, fstab was all ready configured before I even sought to get it set up. So what I was doing was sound in respect of sitting in ubuntu and "sending" my files to windows. For my next set-up, if I do the same and install what you pointed out, I can the do the reverse with the software when using my windows partition. I think I get it now.

One more question, the program is talking about ext2. I thought lucid was ext3. Will I bump into compatibility issues?

---

### Post by ChemShock on 2010-08-27
So I got the ubuntu to xp to work, can you guys help me with the other way around part? The troubleshooting guide on the website just assumes I know windows command prompt. I have no clue on how to get past the after installation screen. Honestly, I'm just an average user that picked all this up as a hobby and all lot of the guides leave you doa (except for the ubuntu pocket guide). Can I get some more help?

---

