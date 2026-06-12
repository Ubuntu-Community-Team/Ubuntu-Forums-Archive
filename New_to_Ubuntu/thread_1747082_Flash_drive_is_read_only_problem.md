---
title: "Flash drive is read only problem"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by HC48 on 2011-05-02
I have been using my TDK 8GB Flash Drive USB for a while with no problems in Windows and Ubuntu. It has suddenly become read only and I can't get it to work. The permissions won't change in preferences and I have checked it out in the disk utility, unmounted, checked and repaired and remounted to no avail. I can see my files but can't add or delete any. I have read the documentation but don't understand this:

**"(USB-Device is, or become suddenly read only without errors**

 If you see  "Write Protect is off" and no errors in your logfiles, than you should  set filesystem type specific mount options (FS_MOUNTOPTIONS) in  /etc/usbmount/usbmount.conf. Wrong gid causes mounting read only.   )"

**Can someone translate please**?:confused: 
 In the terminal **dmesg** gets this:

[12933.713339] scsi 15:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[12933.716909] sd 15:0:0:0: Attached scsi generic sg4 type 0
[12934.133238] sd 15:0:0:0: [sdc] 15630336 512-byte logical blocks: (8.00 GB/7.45 GiB)
[12934.133725] sd 15:0:0:0: [sdc] Write Protect is off
[12934.133730] sd 15:0:0:0: [sdc] Mode Sense: 23 00 00 00
[12934.133733] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[12934.138601] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[12934.138609]  sdc: sdc1
[12934.172636] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[12934.172645] sd 15:0:0:0: [sdc] Attached SCSI removable disk
[12935.796560] FAT: Filesystem error (dev sdc1)
[12935.796567]     invalid access to FAT (entry 0x03e2ac8a)
[12935.796572]     File system has been set read-only


Any help would be appreciated!

HC

---

### Post by wigout on 2011-05-02
I can't translate the gid message for you. I'd like to hear that one myself.

Here's someone else who had that problem points to this thread as their solution:
[http://ubuntuforums.org/showthread.php?p=616396#post616396](http://ubuntuforums.org/showthread.php?p=616396#post616396)

Here's what they said:
> When I upgraded my system to KDE 3.5, i met some problems to mount my  usb drive automatically. When I go to media:/ it always return no such  device. 
At last, I found the solution :razz: 
1. Open your      Code:
     /etc/fstab 
 using your favourite editor. 
    Ex:      Code:
     sudo kate /etc/fstab 
2. Add these lines into the fstab file :
         Quote:
                                                 sysfs        /sys         sysfs     defaults     0    0
usbfs         /proc/bus/usb     usbfs      defaults     0     0
none         /dev/shm     tmpfs     defaults     0     0
none        /dev/pts     devpts     defaults     0     0                                 
3. reboot.
4. That's all folks
Hope that's help.. :grin:and the vote in favor of this solution for a perpetual read-only usb:
> You are THE MAN!!!  I added those lines to fstab and now I can r/w to my  flash drive w/ no problems.  Tried unmounting, then plugging back  in.....no problems.
Thanks for your help!!

---

### Post by Chronon on 2011-05-03
Make sure the file system isn't damaged.  Damaged file systems are usually mounted as read-only to prevent further damage.

The following line adds support for this explanation:
> [12935.796560] FAT: Filesystem error (dev sdc1)

---

### Post by HC48 on 2011-05-04
Thank you for your help but I'm not very good with commands and afraid to do something wrong. 
I did try to do (like mamato in wigout's post above) :
/etc/fstab 

then

sudo (my name) /etc/fstab (I'm the only person in the group and administrator)

and I got:

me-desktop:~$ sudo me /etc/fstab
sudo: me: command not found
me-desktop:~$ /etc/fstab
bash: /etc/fstab: Permission non accordée (= permission not granted:I'm in France)
me -desktop:~$ sudo /etc/fsatb
sudo: /etc/fsatb: command not found

I should be grateful for any more help so that I could check my file system as suggested by Chronon. I am still checking out commands and how tos so a reliable 'recipe' would be really helpful. I did use the disk utility so I'll try again that way.

HC

later after another disk utility check, still no change.

---

### Post by roger_1960 on 2011-05-04
Mmm

If you are using 10.04 I suggest that gedit rather than kate would work as a command, so it should be > sudo gedit /etc/fstab  I think kate is the name of an alternative editor programme!

---

### Post by HC48 on 2011-05-05
aahh! That just proves how little knowledge I have! I didn't get the 'kate' command.
Thank you roger_1960
I'll try again, but later.

HC

---

### Post by Dlambert on 2012-08-27
> **wigout said:**
> I can't translate the gid message for you. I'd like to hear that one myself.

Here's someone else who had that problem points to this thread as their solution:
[http://ubuntuforums.org/showthread.php?p=616396#post616396](http://ubuntuforums.org/showthread.php?p=616396#post616396)

Here's what they said:
and the vote in favor of this solution for a perpetual read-only usb:

This worked for me. Get an error at boot though.

---

