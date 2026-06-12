---
title: "Dual boot Karmic and Lucid"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by occams_beard on 2010-05-08
I'd like to upgrade to Lucid, but here is my dilemma -  I have dozens of things set up just the way I want along with a development environment that I cannot really afford to have any downtime with. Doing a dist upgrade is just not an option (I got burned by that once before) and it would take me days to do a fresh install and get things set up the way I want again.

Now, the box is set up so that a half of my 500 GB hard drive is partitioned for Vista, and another half has Karmic.  I never use Vista, so I would like to just delete the vista partition (it is on a primary partition) and install Lucid, thereby dual booting with karmic and gradually move things over to Lucid as time allows.

Is this possible? Are there any pitfals, will Grub freak out?

Thanks

---

### Post by WinterRain on 2010-05-08
Grub should have no problem with karmic. Just make sure to run the updates immediately after installing.

---

### Post by occams_beard on 2010-05-08
Which grub would be the active grub, the one from karmic or lucid?  Is there any way I can make a boot up disk incase things go south and I can't boot up back into karmic?


My current partition scheme looks like this 

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       21677   174080340    7  HPFS/NTFS
/dev/sda3           21678       60801   314263530    5  Extended
/dev/sda5           21678       42074   163838871   83  Linux
/dev/sda6           42075       42839     6144831   82  Linux swap / Solaris
/dev/sda7           42840       60801   144279733+   7  HPFS/NTFS



```

Vista is on /dev/sda2.  Would installing Lucid screw up the sda numbers?

---

### Post by quadproc on 2010-05-08
> **occams_beard said:**
> ...
Now, the box is set up so that a half of my 500 GB hard drive is partitioned for Vista, and another half has Karmic.  I never use Vista, so I would like to just delete the vista partition (it is on a primary partition) and install Lucid, thereby dual booting with karmic and gradually move things over to Lucid as time allows.

Is this possible? Are there any pitfals, will Grub freak out?

Thanks
There is a potential problem that might affect your plans if you have an ASUS mother board.  Most ASUS MBs include a BIOS which offers something called Express Gate; this is actually a minimal linux system which is intended to allow the user to run things such as Skype without having to do a complete login.  It turns out that only the premium ASUS MBs include that code in the mother board firmware; the rest of the MBs put that code on one of your disks!  So, if you have one of those MBs and you change the disk to put a decent filesystem on it, you will lose at least part of the Express Gate capability.  This may not be important in your case; the system will run without those files but it does announce that installation was incomplete unless you turn off Express Gate in the BIOS.

quadproc

---

### Post by ranch hand on 2010-05-08
I would leave sda1, it is small and you won't miss the space.

Wipe sda2 as it is a waste of space.

Resize sda3 so that it includes the space that is taken up by sda2 currently.

Install 10.04 on the now free space at the beginning of sda2.  I would really use 2 partitions for that.  A separate /home is a good thing to have.

There is very little chance that you will have trouble with grub.  As it is worrying you, here are some things to consider.

System>Administration>Startup Disk Creator

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

During install, after setting things up, you get to the screen to approve installing.  There is an "advanced" button there.  If you click on it you can choose to not have grub install on any drive.  This will mean you can't boot to your new install but you will be able to boot to 9.10, run;
```

sudo update-grub

```
and that should hve you up and running on both.

I would go with the grub from 10.04.  It runs grub1.98 as opposed to grub1.97beta4 under 9.10.  It is better.

---

### Post by occams_beard on 2010-05-08
Worked perfectly, thanks! :)

I actually just let the installer install the 1.98 version of grub and it picked up my karmic install just fine.

First time I haven't had any trace of a Microsoft OS on my machine in years and years, and I won't miss it one bit.

---

### Post by ranch hand on 2010-05-08
You will also have less problems with your box.  Your HDD will probably be quieter too.

---

