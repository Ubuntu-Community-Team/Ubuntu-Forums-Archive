---
title: "[SOLVED] Get rid of GRUB - Already formatted away Ubuntu 7.10"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by halberdier25 on 2008-12-27
Still a total newbie at this...

I formatted away Ubuntu 7.10, but didn't realize that GRUB would still be there.

Now I get an error:

```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22
_
```

How do I go back to Windows?

Thanks!

---

### Post by w4ett on 2008-12-27
insert your windows disk and fixmbr

---

### Post by HotShotDJ on 2008-12-27
This will get you fixed up with minimal hassle: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by halitech on 2008-12-27
if you have your windows install cd, you can boot from that into the recovery console and at the prompt, type fixmbr and that will restore the MBR. if you don't, you'll need something like supergrub to repair the master boot record

---

### Post by taurus on 2008-12-27
If you have a windows CD, boot from it and fix the MBR, /fixmbr.  Otherwise, look at this link, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by nhasian on 2008-12-27
A) Using a DOS or Windows 9x/ME Boot Floppy

In case you have DOS or Windows 9x/ME on your system, you can use fdisk for this purpose. Create a rescue disk in DOS or Windows 9x/ME, use it to boot the computer, and execute fdisk as follows:

fdisk /mbr

The MBR will be rewritten and GRUB will be uninstalled.

B) Using Windows XP

In Windows XP, you can uninstall GRUB as follows:

Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console. Select your Windows XP installation from the list and enter the administrator password. At the input prompt, enter the command "FIXMBR" and confirm the query with "y". The MBR will be rewritten and GRUB will be uninstalled. Press "exit" to reboot the computer.

C) Using Windows 2000

In Windows 2000, you can uninstall GRUB as follows:
Boot from the Windows 2000 CD and press the "R" key during the setup and then the "K" key in the following menu in order to start the Recovery Console. Select your Windows 2000 installation from the list and enter the administrator password. At the input prompt, enter the command "FIXMBR" and confirm the query with "y". The MBR will be rewritten and GRUB will be uninstalled. Press "exit" to reboot the computer.

quoted from [http://www.blogmanno.com/?q=node/9](http://www.blogmanno.com/?q=node/9)

---

### Post by 5BallJuggler on 2008-12-27
put in your windows disk, 
make sure your computer is set to boot from CD in the BIOS
turn off PC and reboot
When you get the option select "R" for repair windows install
select the OS that you are using, normally option 1
at the command prompt type fixmbr.
read the disclaimer and press "y".

that should do it, but......
the 1st time I did this, it did not work, i had to do the same again.

---

### Post by halberdier25 on 2008-12-27
I do not have a Windows disk, but rather a partition.

I attempted using the Super Grub Disk, but it's less than easy to figure out, and I'm not exactly sure what all the options mean.  I've gotten to the point where it asks me what OS I had installed before I got Linux, but all it has is "Syslinux".

Any other way to do this?

Thanks.

---

### Post by 5BallJuggler on 2008-12-27
My suggestion is borrow a disk from a friend, 

not sure if this right, but i think you can use an XP disk or Win2000 disk to repair any version of windows,except maybe vista

you may also be able to repair from a floppy if your machine has a drive, but i'm not sure how.....sorry.

---

### Post by Norm24 on 2008-12-27
If you don't have a XP cd this might be a solution:

[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

---

### Post by w4ett on 2008-12-27
Windows restore disks are also available from your machine's manufacturer...check the support section of the Mfg's Website for details:

For Example: [https://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form](https://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form)

---

### Post by teh_yodeler on 2008-12-27
USE GAG!!!

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

No need for a Windows CD or anything - just download it, burn the iso, boot from it, and point it at your windows partition.  No more worries!!

Plus, you can keep it if you install ubuntu again.  Just tell ubuntu to install grub to the ubuntu partition (click "advanced" on the last installation step, IIRC.

btw, Grub sucks.  It almost turned me off of ubuntu forever

:P

If you need more help with GAG, just post in this thread.  But i'm pretty sure you'll be able to figure it out after you get it booted.  GAG is awesome and has saved me many times.

---

### Post by halberdier25 on 2008-12-27
GAG worked!

Thanks so much!

That was *much* easier than Grub, and in color!

---

### Post by teh_yodeler on 2008-12-27
Glad to hear it friend!! The great thing about GAG is that it's really an operating system boot manager, while grub is a kernel manager.  Grub should stay on the linux partition, it is really a drag when it wipes out the windows bootloader and just stays there after ubuntu has been uninstalled.  You can use GAG to load up to nine different operating systems, and it's an absolute cinch to set up.


P.S., under the GAG setup, you can choose the option "Install Boot Timer."  This will bring you back to the selection panel, where you can press the key for your OS of choice.  Set the "number of seconds" to 20 (or whatever number you wish) and GAG will automatically boot your OS after that number of seconds.

To mark your thread as solved, make sure you're logged in and click on "Thread tools" at the top of the thread.  Then just choose "Mark as Solved," that way people with the same problem will know they've got an answer here.

Cheers!

---

