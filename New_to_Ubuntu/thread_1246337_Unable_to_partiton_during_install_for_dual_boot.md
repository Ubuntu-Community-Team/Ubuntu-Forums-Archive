---
title: "Unable to partiton during install for dual boot"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by samsi on 2009-08-21
Apologies for the length of this post

I have a Compaq netbook with Windows XP installed on a 60GB hard disk.
I was able to install Ubuntu as a dual boot using WUBI - which re-partitioned the hard drive during installation and put Ubuntu into a new 17GB partition


However I now want to install Ubuntu Netbook remix - which I have on a USB stick
I uninstalled the original Ubuntu and started a new install from the USB drive
This is OK up to step 4 of 7 - where I expected to find "Guided" partition options, but only see the following 3

Use entire disc
Use largest contiguous free space
Specify partition manually

Option 1 would wipe out XP and option 2 is not possible as the free space available is only 7.8MB

I don't mind trying to create a manual partition but when I go choose this option I cannot seem to get any further
If I select "New partition table" which is about the only option - I get a screen showing 60022MB of free space but then if I continue I get an error box "No root file system is defined -please correct this from the partition menu-"

Have I missed something basic - or would I be better off using a partitioning tool in XP to create the partition for Ubuntu?

Regards

---

### Post by Penguin Guy on 2009-08-21
> **samsi said:**
> If I select "New partition table"...
Firstly; [COLOR="Red"]do **not** create a new partition table, it wipes your entire disk[/COLOR].
Secondly, if you used WUBI then you wouldn't have needed to make new partitions.
Thirdly; please boot Linux, run [COLOR="Green"]sudo fdisk -l[/COLOR], and post the results back here.

[COLOR="Green"]sudo fdisk -l[/COLOR] gives us info about your HDD which may give us a clearer picture of what is going wrong.

---

### Post by kaptain0 on 2009-08-21
you were doing the right thing mostly. he's right, do not create a new partition table. from manual, just edit the existing ubuntu partition and change from 'do not use partition' to the file system you want to use, and define it as / partition.
 
i've done this dozens of times and it's worked everytime.
 
you don't need to fdisk if your parting with the install cd
 
edit: select the ubuntu partition to get the 'edit' option. that may be why 'create new partition table' was the only option

---

### Post by samsi on 2009-08-21
Thank you both for the very quick replies

First - The original installation using WUBI  created a partition for Ubuntu, this was via windows XP and when I deleted Ubuntu (to install the Netbook Remix from my USB drive) the partition was deleted also

So I cannot edit the Ubuntu partition as suggested by kaptain0 - sorry!
Although strangely I still get the dual boot option at start-up

**Re the sudo fdisk info**  - I ran this on the netbook (I am writing this on another PC) from the USB drive direct using the Terminal 

Not sure how to get the info from there to here - but looking at the screen now the results say the following

Probably you selected the wrong device

Device    Boot          Start            End       Blocks         Id    System
/dev/sdb1 ?             1049447   2022496   979374166    66     Unknown
Partition 1 has different physical/logical beginnings (non-linux?)
     phys=(734,   123,  140 LOGICAL=(1049446,  20,  47)
Partition 1 has different physical/logical endings:
     phys= (120,  143,   6)  logical=(2022495,    32,   9)
Partiton 1 does not end on cyliner boundary.


Then goes on to give similar info for Partition 2, 3 and 4  !!!!

Then ends
Partition table entries are not in disk order


Not sure why it is seeing 4 partitions !!!!

More info

Before I tried to install I defragged and ran CHKDSK in Windows  -

Also used GParted (from the USB drive) which shows the following

/dev/sda1  ntfs  SIze  55.89GiB (of which used is 10.99GiB and 44.90 GiB boot)

underneath is an unallocated partition of 7.84 MiB

If I select the big partition and then Resize/Move I can only alter it by the value of the unallaocted partition i.e. 8 MiB

Also have tried to load Unbuntu from a DVD from a magazine - and get stuck at the same point in the install process (step 4 of 7) - so looks as if the problem is in my hard drive.

Hope this all makes sense
regards

---

### Post by kaptain0 on 2009-08-22
really, 45 GB for boot? i wish i could help more but i can't tell what that means. 
 
otherwise it sounds like your doing the right thing. i think the the extra-large boot partition is a translation issue between linux and windows. they sometimes list each other's details differently.

---

### Post by samsi on 2009-08-22
Hi
here is the full result - had to set up my wireless access to be able to paste it

regards

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bfc1bfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 1055 MB, 1055391744 bytes
33 heads, 61 sectors/track, 1024 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes
Disk identifier: 0x8ef631df

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     1049447     2022496   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(1049446, 20, 47)
Partition 1 has different physical/logical endings:
     phys=(120, 143, 6) logical=(2022495, 32, 9)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?     1713539     3672971  1972168331    7  HPFS/NTFS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(1713538, 15, 31)
Partition 2 has different physical/logical endings:
     phys=(784, 0, 13) logical=(1539355, 11, 19)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     1629317     2599739   976730017   7d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(252, 59, 46) logical=(1629316, 9, 22)
Partition 3 has different physical/logical endings:
     phys=(139, 118, 4) logical=(466123, 13, 24)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     2076186     2080321     4161550   6f  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(2076185, 22, 46)
Partition 4 has different physical/logical endings:
     phys=(10, 114, 13) logical=(2080320, 11, 61)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by samsi on 2009-08-22
Update

To get round the problem I decided to create a partition in XP using Paragon Partition Manager 10 Express to create a 15GB partition

Started the install of Ubuntu Netbook Remix from the USB drive and this time in "Step 4" I could see the reduced XP partition and the new one - good!
Also the options had changed - good!
The first one now offered "Install side by side Choosing between at startup" excellent!

Used this option and the installer offered me a 2.6GB slice of the XP partition - not the new one I had created - not so good!
As I could not see how to use the new empty partition I went with the one offered but used the slider to increase the size to 15GB

UNR installed into this with now problems  - very good!

However when I tried to go back to XP - the boot only got as far as the logo then restarted  - bunmmer!

Am now re-installing Windows

---

