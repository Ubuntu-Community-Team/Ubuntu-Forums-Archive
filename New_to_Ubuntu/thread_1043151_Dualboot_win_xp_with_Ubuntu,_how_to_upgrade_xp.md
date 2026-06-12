---
title: "Dualboot win xp with Ubuntu, how to upgrade xp"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by babloo75 on 2009-01-18
Hi friends
I have a dual boot Win XP with Ubuntu 8.10.
Can I format my windows partition (without formatting Ubuntu) and then install a new copy of Win XP over that same free space left by older XP on the hard disk.
I don't want to lose my Ubuntu 8.10 installation, but want to change my XP only.
Thanks in advance.

---

### Post by superprash2003 on 2009-01-18
this should help [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by arjuntank on 2009-01-18
> **babloo75 said:**
> Hi friends
I have a dual boot Win XP with Ubuntu 8.10.
Can I format my windows partition (without formatting Ubuntu) and then install a new copy of Win XP over that same free space left by older XP on the hard disk.
I don't want to lose my Ubuntu 8.10 installation, but want to change my XP only.
Thanks in advance.

which boot-manager do u use?
if its xp, it wont be a problem..
if grub is not installed on mbr, it would be easier

---

### Post by babloo75 on 2009-01-18
> **arjuntank said:**
> which boot-manager do u use?
if its xp, it wont be a problem..
if grub is not installed on mbr, it would be easier

its grub.
sudo fdisk -l output is

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6075    48749242+   7  HPFS/NTFS
/dev/sda3            6076       30393   195334335    f  W95 Ext'd (LBA)
/dev/sda5            6076        6337     2104452   82  Linux swap / Solaris
/dev/sda6           19129       24227    40957686    7  HPFS/NTFS
/dev/sda7           24228       30393    49528363+   7  HPFS/NTFS
/dev/sda8            6338       18602    98518581   83  Linux
/dev/sda9           18603       19128     4225063+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by babloo75 on 2009-01-18
> **superprash2003 said:**
> this should help [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

couldn't understand anything there..
is there an easy alternative?

---

### Post by arjuntank on 2009-01-18
> **babloo75 said:**
> its grub.
sudo fdisk -l output is

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6075    48749242+   7  HPFS/NTFS
/dev/sda3            6076       30393   195334335    f  W95 Ext'd (LBA)
/dev/sda5            6076        6337     2104452   82  Linux swap / Solaris
/dev/sda6           19129       24227    40957686    7  HPFS/NTFS
/dev/sda7           24228       30393    49528363+   7  HPFS/NTFS
/dev/sda8            6338       18602    98518581   83  Linux
/dev/sda9           18603       19128     4225063+  82  Linux swap / Solaris

Partition table entries are not in disk order

which dell laptop do u have?
the dell partition there really messes things up..
i recommend u to install grub in the partition which has ur ubuntu
next install xp, which will install its boot manager on mbr..
then configure boot.ini in xp to look for partition which has grub installed..
for that u need to make an image of the partition by using the live cd of ubuntu( any *nix) and type:
```

dd if=/dev/sda1 of=/tmp/linux.bin bs=512 count=1

```
replace sda1 with the partition u have grub installed..
copy the linux.bin from /tmp and paste to any removable drive or any other partition mounted
now the task is simple, just copy linux.bin to windows root directory and edit boot.ini and add the path of linux.bin to the entry
u can also edit boot.ini to add dell media direct ( if u have one )

isnt this simple or more confusing?

---

### Post by TJCIB on 2009-01-18
Unfortunately that *is* the easy way.

You should be able to follow those steps outlined on the top of that link.  Steps 1 through 5 should do it for you.

Install XP on your XP partition, usually it is the first one if XP was installed first.

Once you reboot, you will not be able to get into Ubuntu, it won't give you the option.  At this point, stick your Ubuntu LiveCD in and reboot into that. Open a terminal in the LIve environment and follow the steps on that page.  It should work.  If not, come back here and ask more questions.

The tricky part in step 4 is that you must see the output of the command and use it in the next command.  Don't worry, it is not that scary.

*EDIT* I missed that DELL partition in there (reading too fast).  That does make things weird.  Not sure if the link is exactly what you need, but it may still work, otherwise the above poster may have the real solution.

---

### Post by babloo75 on 2009-01-18
> **arjuntank said:**
> which dell laptop do u have?
the dell partition there really messes things up..
i recommend u to install grub in the partition which has ur ubuntu
next install xp, which will install its boot manager on mbr..
then configure boot.ini in xp to look for partition which has grub installed..
for that u need to make an image of the partition by using the live cd of ubuntu( any *nix) and type:
```

dd if=/dev/sda1 of=/tmp/linux.bin bs=512 count=1

```
replace sda1 with the partition u have grub installed..
copy the linux.bin from /tmp and paste to any removable drive or any other partition mounted
now the task is simple, just copy linux.bin to windows root directory and edit boot.ini and add the path of linux.bin to the entry
u can also edit boot.ini to add dell media direct ( if u have one )

isnt this simple or more confusing?

i have Dell Optiplex 330 desktop.
Thats all i could understand...
(have no knowledge about partitions..)

---

### Post by babloo75 on 2009-01-18
> **TJCIB said:**
> Unfortunately that *is* the easy way.

You should be able to follow those steps outlined on the top of that link.  Steps 1 through 5 should do it for you.

Install XP on your XP partition, usually it is the first one if XP was installed first.

Once you reboot, you will not be able to get into Ubuntu, it won't give you the option.  At this point, stick your Ubuntu LiveCD in and reboot into that. Open a terminal in the LIve environment and follow the steps on that page.  It should work.  If not, come back here and ask more questions.

The tricky part in step 4 is that you must see the output of the command and use it in the next command.  Don't worry, it is not that scary.

*EDIT* I missed that DELL partition in there (reading too fast).  That does make things weird.  Not sure if the link is exactly what you need, but it may still work, otherwise the above poster may have the real solution.

Couldn't understand this too. Can you please explain it in detail.
Sorry, I have little knowledge of computing/ linux

---

### Post by balaknair on 2009-01-18
Step 1: Backup all important data on your hard drive, defragment the WinXP partition(C:\) 

Step 2: Install Windows XP using the Windows (I guess you know how to do this, right?) as you would normally do from the CD to the partition where you already have windows installed.

IMPORTANT: Make sure that windows is installed to the original Windows partition and the Linux partition is untouched.

Step 3: You should now be able to start up the PC and boot into Windows.

Shut down the PC.

Step 4: Now you need to recover/repair the Ubuntu boot menu. For this boot the PC into the Ubuntu LiveCD---> When you get to the desktop, open a Terminal(Applications menu> Accessories> Terminal), and type in or copy/paste the following commands one by one
```
sudo grub
find /boot/grub/stage1
```

This gives you an output which will look like this (hdX,Y)- for eg: In your case since the Linux partition is sda8, GRUB will see it as (hd0.7)
*Replace* X,Y *in the step below with the numbers you get--> eg*: 0,7


```
root (hdX,Y)
setup (hd0)
quit

```



Reboot and remove the CD. GRUB should now be installed as it was before.

---

### Post by balaknair on 2009-01-18
If all the commands scare you, you can use something call Auto Super Grub Disk.

After installing Windows, boot into Windows.

1) Download Auto Super Grub Disk here [http://forjamari.linex.org/frs/download.php/1131/auto_super_grub_disk_1.5.exe](http://forjamari.linex.org/frs/download.php/1131/auto_super_grub_disk_1.5.exe)

2) Install it by double-clicking on the file(you may need to disable your antivirus temporarily, since ASGD has to be added to start-up to fix the MBR).

3) Just click OK at each step of the install, till it asks you to reboot.

4) Now when you boot up, you will see an option "**unetbootin-supergrubdisk**" along with the Windows option. Select unetbootin and press 'Enter'

5) Now the ASGD will scan your hard drive, find the GRUB menu.lst in the Ubuntu partition, and will load it, so that you can see the same GRUB menu you had before reinstalling Windows. Choose Ubuntu from the list and boot it.

6) After booting into Ubuntu, you should now reboot again.

7) When you see the GRUB menu this time, choose Windows, and once you have logged in to Windows, the ASGD wizard will ask if you want to remove unetbootin from the boot menu. Choose 'YES'.


That's it. You're done. No interaction beyond clicking 'OK' or 'Next'

---

### Post by babloo75 on 2009-01-19
Thanks dear. will follow the steps as you have explained.

---

### Post by babloo75 on 2009-01-19
> **balaknair said:**
> Step 1: Backup all important data on your hard drive, defragment the WinXP partition(C:\) 

Step 2: Install Windows XP using the Windows (I guess you know how to do this, right?) as you would normally do from the CD to the partition where you already have windows installed.

IMPORTANT: Make sure that windows is installed to the original Windows partition and the Linux partition is untouched.

Step 3: You should now be able to start up the PC and boot into Windows.

Shut down the PC.

Step 4: Now you need to recover/repair the Ubuntu boot menu. For this boot the PC into the Ubuntu LiveCD---> When you get to the desktop, open a Terminal(Applications menu> Accessories> Terminal), and type in or copy/paste the following commands one by one
```
sudo grub
find /boot/grub/stage1
```

This gives you an output which will look like this (hdX,Y)- for eg: In your case since the Linux partition is sda8, GRUB will see it as (hd0.7)
*Replace* X,Y *in the step below with the numbers you get--> eg*: 0,7


```
root (hdX,Y)
setup (hd0)
quit

```



Reboot and remove the CD. GRUB should now be installed as it was before.

I find this method easy to understand.
In step 2 above, can you be little more informative. I mean should i boot computer through Win XP CD first and then install it (with or without formatting the drive); or should I open computer in Win XP and then insert Win XP CD and install that. As far as I remember, if we do the second option then the CD asks for a fresh install or an upgrade over the old installation. Which option should i follow first. 
Thanks in advance.

---

### Post by balaknair on 2009-01-19
You can use either method, whichever you're comfortable with. Use the 'upgrade' or 'reinstall' option since I think in a fresh install you might need to format the partition choosing the C:\ drive manually(it's been a long time since I reinstalled XP).

---

