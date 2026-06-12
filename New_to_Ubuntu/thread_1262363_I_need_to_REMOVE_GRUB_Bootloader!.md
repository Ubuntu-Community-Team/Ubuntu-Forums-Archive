---
title: "I need to REMOVE GRUB Bootloader!"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Spoken on 2009-09-09
Basically, through a series of trails / mistakes / and unfortunate events, im left with a unbootable computer on my hands.

I have vista home premium installed on the entire harddrive (using recovery disks, i dont have a "install cd" just the recoverys), however, i cant bootup because the grub bootloader is still present eventhough i deleted my other linux partition.  Is there a way to remove grub from the terminal using a linux live cd?

or what other options do i have?

(NOTE: I have been informed that i could re-install ubuntu , then just edit the menu.lst to hide grub?, then re-install vista from the recovery cds (i have the microsoft key).  Can anyone confirm this as a proven method?  I could do this as its a new computer and i dont have any information or files on it that i care about.

(NOTE #2: For all linux enthusiasts that wont answer my question but post stuff anyways like "why would u delete linux?"....i will return to linux shortly, so please...just help me lol"

---

### Post by Darkwing-Duck on 2009-09-09
Try this and see if it works for you...
 
1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr, and then press ENTER.

That's it. Now when you reboot your PC, Vista will load automatically...
 
If you need any more help just post away.

---

### Post by eagle416 on 2009-09-09
if you can't use your windows cds or recovery disks to restore grub, you would't want to remove it.

Note1: I had a similar problem. I reinstalled ubuntu so I could get grub all the way back. Then I could boot into windows. From inside windows I installed/used the recovery console. google restoring windows mbr and follow instructions. When you have the windows bootloader restored, ubuntu is inaccessable, computer only boots into windows. Simply use a Linux LiveCD and a partition editor to destroy all ubuntu partitions, and you should be good.

---

### Post by desperado665 on 2009-09-09
If you re-install windows from your recovery discs, it should overwrite grub with the windows boot-loader... problem solved.

> 
1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr, and then press ENTER.

That's it. Now when you reboot your PC, Vista will load automatically...


+1

---

### Post by Spoken on 2009-09-09
the entire hard drive is taken by the vista partition, but the grub bootloader still exists from the previous linux partition. so if i reinstall ubuntu, grub will work correctly and i could get into windows and or ubuntu when i wanted correct? (basically, a working dual boot setup?)

EDIT: The recovery disks dont work the same as the install cd does, i cant just throw them in and use a command "fixmbr" or anything, cause a prompt is never given to me.

---

### Post by HousieMousie2 on 2009-09-09
A dual boot should get you what you want... access to Windows (and Ubuntu)

Or you can do as Wonderly suggested and use your recovery CD to create a new Master Boot Record... which will give you back Vista (but not Ubuntu.)

Then it looks like reinstalling Ubuntu would be the quickest/easiest option.

---

### Post by halitech on 2009-09-09
look at supergrub

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by HousieMousie2 on 2009-09-09
SuperGRUB is supposed to be capable of repairing the Windows MBR... I did not have any luck with it myself, but that was a ways back and it is certainly worth a shot.

---

### Post by Spoken on 2009-09-09
im currently in the process of re-installing ubuntu on half of the hard drive, so, in theory, this should get grub working again, and since vista is already installed on the drive, when i boot up through grub, i should be able to boot into either.

ill keep you posted on the results.

---

### Post by raymondh on 2009-09-09
Or you can try either of these to access a command prompt

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Yes, dual-booting will also work.

Good luck.

---

### Post by sandyd on 2009-09-09
> **raymondhenson said:**
> Or you can try either of these to access a command prompt

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Yes, dual-booting will also work.

Good luck.
+1
the first link fixed it when i had the same problem:P

---

