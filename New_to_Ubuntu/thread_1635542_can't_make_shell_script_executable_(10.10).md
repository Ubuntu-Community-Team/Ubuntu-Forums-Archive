---
title: "can't make shell script executable (10.10)"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by meadhikari on 2010-12-01
The script that is shown executable in my Hard disk becomes un executable when copied to the pen drive.

When I went through to solve the problem I found this but seriously I as a newbie could not understand a bit of it.

> Probably related to this (though there is another possibility.
To resolve a bug in udisks this patch was added - applies to vfat filesystems on removable media


Add 00git-vfat-showexec.patch: Enable the "showexec" vfat mount option, to
avoid data files being executable (which causes confusing question dialogs
in nautilus which only have one sensible answer). Patch taken from
upstream git head. (LP: #14335)

The patch can be reverted in a custom udisk build - if this is your issue


Please help me solve this.

This basically is a auto-run script that I want to run. Is there any way to trigger that script automatically from the hard disk when the pen-drive is inserted.

---

### Post by CharlesA on 2010-12-01
What file system is on the thumb drive? FAT and NTFS do not support Linux file permissions (rwx).

---

### Post by meadhikari on 2010-12-01
Yes my file system is FAT but what other file system is supported both in Windows XP and also has permission in Ubuntu

---

### Post by CharlesA on 2010-12-02
There's ext2 and ext3, but Windows XP needs a third-party driver to read/write to it.

---

### Post by mc4man on 2010-12-02
> Is there any way to trigger that script automatically from the hard disk when the pen-drive is inserted.
Well there are a couple of ways to do that but I'm wondering if you can't find another way. (there's always a possibility of unintended consequences or use with something like this.
As I remember there is (or was) a windows prog. that allowed reading/writing to ext.2, though the name eludes me atm. Maybe search that out.
Otherwise there are 3 ways around this, if still inclined I'll mention 2 of them

---

### Post by meadhikari on 2010-12-02
> Otherwise there are 3 ways around this, if still inclined I'll mention 2 of them

Please.

As I also wanted to make one of my script work for my Bluetooth connected mobile phone to automatically sync with my Hard Disk. I have the script but the automatic part of it is missing

---

### Post by mc4man on 2010-12-02
can think of 4 ways, 2 very safe - 
rebuild nautilus to revert the  new vfat mount options, only downside is it treats all files as executable, though that is merely a slight annoyance. Fairly easy to do if you wish.

open a terminal and go 
bash /path/to/scriptname

Ex. - runs a script named vlccd1 on a fat32 pen drive
bash /media/D2A2-9FDB/vlccd1

To auto run a udev rule could be best but a bit to complicated

so finally -
Open your pen drive, create an **empty** text file named autorun
Remove the drive and then re-insert, you'll get a pop up.

From the pop up choose 'Open with other application' -> 'use a custom command'
If your script is in a bin folder in your path (~/bin, /usr/local/bin, /usr/bin) then just enter the scriptname. Otherwise or even if in a bin use the browse button to locate.
Then click add.

I suggest **not ** to ck. the 'Always perform...' box, leave it as a pop up choice. You can add other scripts to the list of available choices in the same manner.

---

### Post by DaithiF on 2010-12-02
> **meadhikari said:**
> 
This basically is a auto-run script that I want to run. Is there any way to trigger that script automatically from the hard disk when the pen-drive is inserted.

I think the previous posts may have missed this point ... you don't have to solve the non-executable mount problem if you leave the script on your hard drive and execute it from there when your usb device is plugged in.  This is indeed possible, and a very common requirement.

There are lots of posts on these forums on how to configure a script to be run when a usb device is plugged in.  Unfortunately a lot are incomplete ... this howto may be a good starting point:
[https://help.ubuntu.com/community/UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto)

---

### Post by mc4man on 2010-12-02
> may have missed this point
actually said this
> To auto run a udev rule could be best but a bit to complicated

Not saying the Op can't figure it out but maybe you missed this

> but seriously I as a newbie ...

---

### Post by meadhikari on 2010-12-03
Thanks for your support but I am not following it.

I could not understand what the sentence below means.

> rebuild nautilus to revert the  new vfat mount options

and also thought of using the udev rule following the link but when I type dmsg I get something else.

I just wanted to execute a script whenever I insert a pen drive and that pen drive should also be able to run in windows xp.

Could you Please Please explain me the other safe option that you were talking about

---

