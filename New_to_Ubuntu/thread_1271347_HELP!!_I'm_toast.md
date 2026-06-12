---
title: "HELP!! I'm toast?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by XKCD64 on 2009-09-20
OMG.  I just installed Ubuntu on an 80GB partition and used the little slider on installation to shrink Windows XP.  I can still see the option to boot into Windows but when I click on it all I get is a black screen!  Please help!

My mom is going to kill me!

---

### Post by Tigersmind on 2009-09-20
Do you have a Windows XP cd or restore disks from your computer maker?

---

### Post by kerry_s on 2009-09-20
sounds like you forgot to defrag first.
your screwed. you should not be installing anything, if the pc is not yours. suck it up & tell your mom you messed up.

---

### Post by XKCD64 on 2009-09-20
Unfortunately, no I don't.

And why was I supposed to defrag?!?!?!  OMG.  No one told me to.  I'm freaking out.  Is there ANYTHING I can do??

---

### Post by hansdown on 2009-09-20
Hi XKCD64.

Just relax. Can you click applications> accessories> terminal?

Copy and paste this in, and we can see how your partitions look.

```
sudo fdisk -l
```

---

### Post by XKCD64 on 2009-09-20
michael@michael-desktop:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         981     7879851    c  W95 FAT32 (LBA)
/dev/sda2             982       19952   152384557+   7  HPFS/NTFS
/dev/sda3           19953       30401    83931592+   5  Extended
/dev/sda5           19953       30051    81120186   83  Linux
/dev/sda6           30052       30401     2811343+  82  Linux swap / Solaris

---

### Post by corncob on 2009-09-20
I don't know if this would work but you might try System > Administration > Partition Editor and see if you could shrink the Linux partition thus giving XP more room.  You might have to do this from the Live CD so as to be able to unmount the partition.
Only other thing I can think of is to explain to Mom how great Ubuntu is before she turns on the computer:)

---

### Post by Tigersmind on 2009-09-20
You need to defrag first so all the data on the partition you resize is in one place. It reduces the chance of corrupting data.

Your computer or your Moms/Family?
If its yours you can always say you like Linux now.....

Edit:
Am I reading this right?
/dev/sda1 * 1 981 7879851 c W95 FAT32 (LBA)
A fat32 followed by a NTFS is in my experience a restore partition

---

### Post by XKCD64 on 2009-09-20
It's a family computer, and I don't know what any of that means.  I'm sorry.  But is there ANYTHING I can do at all?

---

### Post by Tigersmind on 2009-09-20
Xk if you are still there, post who makes your system (HP, Dell) and model,
Mine is an HP so it says Pavilion A767C on it. Something like that.

---

### Post by XKCD64 on 2009-09-20
Compaq Presario SR165ONX

It's kind of old.

---

### Post by Tigersmind on 2009-09-20
> **XKCD64 said:**
> It's a family computer, and I don't know what any of that means.  I'm sorry.  But is there ANYTHING I can do at all?


Thats fine it was more of a general question for anybody. Sorry for the bad wording.

Its possible it will run XP again, but my concern at the moment is the stuff in XP. Any thing there that would need backed up? If so its better to get the one you have running instead of using a restore partition. (if it is one)

---

### Post by XKCD64 on 2009-09-20
No.  I can (at boot up) select Windows XP, but all I get is a black screen.  And after like 5 minutes I just turn off and booted into Ubuntu to post here.

---

### Post by Tigersmind on 2009-09-20
> **XKCD64 said:**
> No.  I can (at boot up) select Windows XP, but all I get is a black screen.  And after like 5 minutes I just turn off and booted into Ubuntu to post here.

Well I looked up your computer. Originally it came with Restore CDs and a Restore partition on the HD. When the computer would boot, you could just pres F10 a few times and the restore would start. This process however would wipe all information on the computer and set it up how it was when it was bought. If F10 didnt work, the CDs could be used too.

If nothing needs to be saved from XP, try pressing F10 when you turn on your computer. Maybe there is a chance that wasnt wiped out. Sounds odd, but I could do that once when I was in about the same boat you are.

If it works, it should undo everything that's been done and wipe everything. Partition changes and all.

---

### Post by empty_spaces on 2009-09-20
Before you try anything else, I would recommend that you access your Wndows partition from Ubuntu and copy/backup all the data there.
Then, find your Windows installation CD and select the option to repair your windows installation.
I don't have much of an idea about recovery partitions, which is what you might have instead of the windows CD.

---

### Post by gradinaruvasile on 2009-09-20
> **XKCD64 said:**
> It's a family computer, and I don't know what any of that means.  I'm sorry.  But is there ANYTHING I can do at all?

First of all: u should have ur data on the XP partition. U should be able to see it. Just click places and click on the hard drive icon (should read X GB Media or have some name like SYSTEM or whatever. Anyways it should open in the file browser.

For the system recovery part:

Try this:

Open a terminal (applications->accessories->terminal .

type:

```
sudo umount /dev/sda2
```

```
sudo apt-get install ntfsprogs
```


press y if asked if ur sure. It is a chance that u have installed the ntfsprogs package, if it sais it is already installed, go on.

```
sudo ntfsfix /dev/sda2
```

Reboot.

PS I see that u have sda1 partition marked as boot partition... AFAIK the second partition (sda2) should be the boot partition because the first one is some sort of recovery partition or something. Dont take my word for it though. 

Post the output of the following command if the above fails:

```
sudo cat /boot/grub/menu.lst
```

---

### Post by Tigersmind on 2009-09-20
> **empty_spaces said:**
> Before you try anything else, I would recommend that you access your Wndows partition from Ubuntu and copy/backup all the data there.
Then, find your Windows installation CD and select the option to repair your windows installation.
I don't have much of an idea about recovery partitions, which is what you might have instead of the windows CD.

Yes, empty is right. If you do need anything you can get it from Linux if needed.

Recovery partitions and restore CD are why I have not got a normal Windows CDs with a computer since about 1998. They are a horrible joke  >.>


My honest opinion is after you fix this run Linux on a Live CD. Try to get your family using it. My computer is old too, but with Linux it runs like a champ.

---

### Post by DarinB on 2009-09-20
I see that you said you are testing karmic koala, if this is so once you get the data backed up through ubuntu, if you go to places you will be able to mount the windows partition and copy all of your documents to a thumb drive or cd, be sure to include your address book for outlook it will be in the windows folder. maybe even your favorites. if you can get the restore partition to work, google dual boot ubuntu with xp there are step by step tutorials. and use a stable version like jaunty 9.04 not karmic still in Alpha not even Beta. All may not be lost just keep your cool and worse comes to worse say you got a terrible virus and had to redo the whole pc. this will keep you up for about 8 or 9 hours. don't worry it happens to all of us at one time or another

---

### Post by gradinaruvasile on 2009-09-20
If u are using Karmic (Ubuntu 9.10) the last command will be:

```
sudo cat /boot/grub/grub.cfg
```

---

### Post by theozzlives on 2009-09-20
> **DarinB said:**
> I see that you said you are testing karmic koala, if this is so once you get the data backed up through ubuntu, if you go to places you will be able to mount the windows partition and copy all of your documents to a thumb drive or cd, be sure to include your address book for outlook it will be in the windows folder. maybe even your favorites. if you can get the restore partition to work, google dual boot ubuntu with xp there are step by step tutorials. and use a stable version like jaunty 9.04 not karmic still in Alpha not even Beta. All may not be lost just keep your cool and worse comes to worse say you got a terrible virus and had to redo the whole pc. this will keep you up for about 8 or 9 hours. don't worry it happens to all of us at one time or another

I don't think lying to your mom is a good idea. Just use the live CD, backup your AND YOUR MOM'S data, and restore the system. Tell your mom you made the mistake of installing a test only version of Ubuntu and would like to install the stable one. Maybe with WUBI.

---

### Post by Old_Grey_Wolf on 2009-09-20
If one of my grandchildren did that to one of my computers, I would probably be LMAO. I keep regular bachups of my computers. 

One of my grandchildren is a teenager. I would find it encouraging that they are exploring the computer, and OS alternatives.

However, if they lied to me about what they did, I would get pissed off. Not for what they did; but rather, that they didn't understand that I am willing **to help them learn from their mistakes in life**.

I would much prefer that they admit what they did. Then we could work together to fix the problem.

If that is a Windows partition on the hard drive, no matter what you do, I don't think it will go unnoticed. You probably lost some email, favourites, etc.

---

### Post by tom66 on 2009-09-20
Try this:

```

sudo mount -t ntfs-3g /dev/sda2 /windowsNTFS -o force

```

Then go to /windowsNTFS in Nautilus or your favourite file manager.

Importantly, if the partition is truly damaged do NOT change anything (file-wise) before you recover important stuff otherwise you could destroy it all.

---

