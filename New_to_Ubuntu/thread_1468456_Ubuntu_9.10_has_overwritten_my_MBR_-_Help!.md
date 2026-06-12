---
title: "Ubuntu 9.10 has overwritten my MBR - Help!"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by lulabelf on 2010-05-01
Help!  Dual installation - Ubuntu 9.10 into Windows XP. I have gotten as far as Terminal, identified that my windows boot (I believe) is in del/sda1.  Not sure what to enter from there to get my windows boot back up and running.  I need to either switch back and forth between Ubuntu and XP or let go of Ubuntu all together.  Miss being able to download movie files from Netflix.  Also can't play VLC media either.  Rats!

Udate of original message

lulabelf

Solved problem by downloading Ubuntu 10.4, and going to medibuntu and opening repository in Terminal.   Now I've got my movies and a little Ubuntu experience under my belt!  Yea for me!    Thanks to all who offered input!

---

### Post by Lazy-buntu on 2010-05-01
What exactly is happening? Does grub show xp? When you try to boot XP do you get a blinking cursor?

I'm having a problem booting into Windows 7 myself: [http://ubuntuforums.org/showthread.php?t=1466038](http://ubuntuforums.org/showthread.php?t=1466038)

---

### Post by lulabelf on 2010-05-01
Hi!  Pardon me for gushing, but your the first person to respond!  I'm not sure what is happening.  I installed Ubuntu 9.10 and it took over.  I'm not sure what a GRUB is and whether or not I have one, but I did find all my XP files within the system.   Don't know enough on how to navigate!   Good luck on your figuring out what's going on with your situation.

---

### Post by Lazy-buntu on 2010-05-01
Try ```
sudo update-grub
``` and let us know what it says :)

---

### Post by relic70 on 2010-05-01
> **lulabelf said:**
> Help!  Dual installation - Ubuntu 9.10 into Windows XP.  Can't find way into XP although I found the files.    In Terminal, don't know what to type any kind of process search.  Can anyone help.  I'm a moderate amature; been stuck for a week now - beginning to hate Ubuntu!   Just want control of my OSs so that I can switch back and forth!!!

lulabelf

You probably need to repair your MBR (master boot record) in your Windows installation.

Search "fix mbr" in Google and you'll find a number of links to that. It requires you to boot into your Windows installation disk and use the Recovery console to enter the command fixmbr.

I've had to do that in the past when I made some error in installation.

Hope that helps

---

### Post by lulabelf on 2010-05-01
Hi.  This is what I got when I went to Accessories/Terminal and pasted in: sudo update grub

[sudo] password for lydia: 

I don't know what it's asking for.  My regular password or another?  At the blinker, nothing I type shows up!

---

### Post by lulabelf on 2010-05-01
> **relic70 said:**
> You probably need to repair your MBR (master boot record) in your Windows installation.

Search "fix mbr" in Google and you'll find a number of links to that. It requires you to boot into your Windows installation disk and use the Recovery console to enter the command fixmbr.

I've had to do that in the past when I made some error in installation.

Hope that helps


I tried this.  Couldn't use my Windows installation disk.  The gist of the message back said that the central directory or signature not found.   Thanks anyway.

---

### Post by zibi on 2010-05-01
It asks for your normal password. Nothing shows up if you type, it's normal. Just type it and press enter

---

### Post by lulabelf on 2010-05-01
> **Lazy-buntu said:**
> Try ```
sudo update-grub
``` and let us know what it says :)

Hi. Sorry, still getting use to using this resource.   When I go to Accessories/Terminal,
I get my usual name & computer info.  However, when I put in the code you suggested, it comes back with this messae:   [sudo] password for lydia:   At that point, I can't enter anything.  The blinker is active but takes nothing.      Is it asking for my regular password or do I need another.    Thank you so much for your patience.   I'm fascinated by the OS, just need to control it.

---

### Post by lulabelf on 2010-05-01
> **zibi said:**
> It asks for your normal password. Nothing shows up if you type, it's normal. Just type it and press enter


Thank you so much!  This is message I got.  Not sure how to proceed.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

---

### Post by zibi on 2010-05-01
close all open applications,  and restart the machine.

---

### Post by admiralspark on 2010-05-01
As another poster pointed out, you WILL NOT SEE YOUR PASSWORD ENTERED. Simply type your password used to login, then hit enter. It does not show so that if anyone was looking over your shoulder, they wouldn't see the password length. It's just more security. 

The "sudo" at the beginning of the command stands for Super User DO, meaning it temporarily grants administrative privileges to anything that comes after it. The next bit, "update-grub", will search your system (quickly) and pick up other operating systems, then add them to Grub2 (the black and white screen that may or may not show up when you boot ubuntu, but definitely will after you do this). It adds all operating systems to a list that will be showed to you when you first start the computer.

After you type ```
sudo update-grub
``` into the terminal and enter your password, some text will display. I'm guessing it'll have two entries that say "Linux-XXX" or "Ubuntu-xxx", then a Memtest, then "Windows XP Bootloader".
EDIT: congrats on getting it working!

EDIT2: Unless you have problems, when wanting to boot Ubuntu select the topmost entry with the highest final number, which is 20 in this case. That is the latest and most secure of the kernels.

---

### Post by lulabelf on 2010-05-01
> **admiralspark said:**
> As another poster pointed out, you WILL NOT SEE YOUR PASSWORD ENTERED. Simply type your password used to login, then hit enter. It does not show so that if anyone was looking over your shoulder, they wouldn't see the password length. It's just more security. 

The "sudo" at the beginning of the command stands for Super User DO, meaning it temporarily grants administrative privileges to anything that comes after it. The next bit, "update-grub", will search your system (quickly) and pick up other operating systems, then add them to Grub2 (the black and white screen that may or may not show up when you boot ubuntu, but definitely will after you do this). It adds all operating systems to a list that will be showed to you when you first start the computer.

After you type ```
sudo update-grub
``` into the terminal and enter your password, some text will display. I'm guessing it'll have two entries that say "Linux-XXX" or "Ubuntu-xxx", then a Memtest, then "Windows XP Bootloader".
EDIT: congrats on getting it working!

EDIT2: Unless you have problems, when wanting to boot Ubuntu select the topmost entry with the highest final number, which is 20 in this case. That is the latest and most secure of the kernels.



Thanks for your indepth response.   However, I just had to shut down that computer completely!    My Microsoft Security flashed to tell me that I'd been hit with trojans and serious viruses.  I couldn't download the 'fix' because Ubuntu didn't recognize the files.  Looks like I have to take my computer somewhere and have the whole thing cleaned up and restored.   This is so disheartening!

---

### Post by lulabelf on 2010-05-01
> **zibi said:**
> close all open applications,  and restart the machine.



Thanks, but just had to shut down computer completely.  Hit with trojans and viruses.  Couldn't download the fix since Ubuntu couldn't recognize the file.   Looks like I'll have to have computer professionally cleaned.

---

### Post by Teber on 2010-05-01
got a similar problem. my boot menu lists just one ubuntu, two memtests and windows xp

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
```

got this response from sudo update-grub

tried booting windows xp again. got a black screen with blinking cursor and complete inactivity. what would be the next step? any help will be appreciated. unless of course this a signal from the Skipper in the Sky to abandon windows altogether...

:)

---

### Post by eriktheblu on 2010-05-01
> **lulabelf said:**
> ...I just had to shut down that computer completely!    My Microsoft Security flashed to tell me that I'd been hit with trojans and serious viruses.  I couldn't download the 'fix' because Ubuntu didn't recognize the files...
This doesn't make sense.

Microsoft should not pop security warnings in Ubuntu.

There are several websites out there that try to imitate MS security software in order to trick user into downloading their software. It's a good thing Ubuntu doesn't recognize those files because they are most likely harmful.

If this is a Wubi install (installed from inside Windows rather than booting from a CD) ignore this:

Here's how it works:
Your BIOS boots a disk by first looking to the disk's MBR for the boot partition. The boot partition needs a boot loader to load the OS. The MS boot loader cannot load Ubuntu (normally) but Ubuntu's boot loader (Grub) can load the MS boot loader.

Following your BIOS initialization, Grub should load with a list of OSs installed on your machine (hold shift during boot if you do not see it). Windows will be at the bottom of the list. Use the arrow keys to select Windows.

---

### Post by lulabelf on 2010-05-01
> **eriktheblu said:**
> This doesn't make sense.

Microsoft should not pop security warnings in Ubuntu.

There are several websites out there that try to imitate MS security software in order to trick user into downloading their software. It's a good thing Ubuntu doesn't recognize those files because they are most likely harmful.

If this is a Wubi install (installed from inside Windows rather than booting from a CD) ignore this:

Here's how it works:
Your BIOS boots a disk by first looking to the disk's MBR for the boot partition. The boot partition needs a boot loader to load the OS. The MS boot loader cannot load Ubuntu (normally) but Ubuntu's boot loader (Grub) can load the MS boot loader.

Following your BIOS initialization, Grub should load with a list of OSs installed on your machine (hold shift during boot if you do not see it). Windows will be at the bottom of the list. Use the arrow keys to select Windows.


Thanks for response.  I paniced and didn't do anything but come back on line through my 2nd computer.  I was wondering how MS could break through like that.  More than likely it is bogus.   In the meantime, I'm not sure if I have a Wubi install. (not clear on terminology yet)   I bought a book on Ubuntu 9.10 and installed from the cd attached.     I actually got into my Terminal and found a list of (I think) boot options.  Windows was the last entry.   So it sounds like I need to select that one.   I would need guidance after that move unless clicking on it will present me with options.

---

### Post by dirty_sailor on 2010-05-01
Fixing your MBR for Windows should be no problem if you have the OS disc.  Boot up off of the Microsoft disc, enter the recovery console, enter your password (if you don't have one, just hit enter) then type fixmbr.  If you don't have the disc, there are places online where you can find the files (check google).

I had a similar problem and don't know how to proceed on my problem, the thread is here: [http://ubuntuforums.org/showthread.php?t=1468312](http://ubuntuforums.org/showthread.php?t=1468312).  If anyone can help me save that install, please let me know!

But fixing the MBR above should work if you want to restore your Windows installation.  I just don't know what it will do with your Ubuntu install...

---

### Post by lulabelf on 2010-05-01
> **dirty_sailor said:**
> Fixing your MBR for Windows should be no problem if you have the OS disc.  Boot up off of the Microsoft disc, enter the recovery console, enter your password (if you don't have one, just hit enter) then type fixmbr.  If you don't have the disc, there are places online where you can find the files (check google).

I had a similar problem and don't know how to proceed on my problem, the thread is here: [http://ubuntuforums.org/showthread.php?t=1468312](http://ubuntuforums.org/showthread.php?t=1468312).  If anyone can help me save that install, please let me know!

But fixing the MBR above should work if you want to restore your Windows installation.  I just don't know what it will do with your Ubuntu install...



Thanks for response.  I don't have original disc.  I tried using a external HD with the necessary files on it, but didn't know how to get Ubuntu to acknowledge the file and open it.

---

### Post by dirty_sailor on 2010-05-01
No one is helping me on my thread, but I feel your pain.  In order to get Windows back, you need that MBR.  Luckily I had the disc so it was only an inconvenience for me.

Apparently there are plenty of ISO images of the XP disc out there, without the installation files of course.  If you can boot off of a disc you make with those files from your second computer, it should only take a second to restore your OS.  Here's a site I found explaining the procedure: [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/).

Sorry, I didn't look for an ISO of XP, but it should be easy to find on google.  Good luck, my friend!

Edit: I don't think you will be able to fix the MBR from within Linux.  I think you have to boot off of the CD.  I don't know that, but I'm pretty sure...

---

### Post by dirty_sailor on 2010-05-01
I haven't tested any of these ideas, but just found them... good luck to you!

[http://forum.eeeuser.com/viewtopic.php?id=77798](http://forum.eeeuser.com/viewtopic.php?id=77798)

---

### Post by oldfred on 2010-05-01
When you installed did you put grub2 into the windows partition?

Windows has a two part boot. All computers start boot from the MBR of the primary master hard drive. IF SATA drives you set primary master in BIOS. Windows boot in MBR starts a second part boot from the PBR or partition boot record or boot sector. Grub also uses that second part to boot windows from grub. Grub normally does not install to a PBR but can be. So if you installed grub to the windows PBR you overwrote the second part of the windows boot loader.

You can repair that with these instructions from Ubuntu or windows repair disk.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows. You would only need to run fixboot command.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by lulabelf on 2010-05-01
> **dirty_sailor said:**
> No one is helping me on my thread, but I feel your pain.  In order to get Windows back, you need that MBR.  Luckily I had the disc so it was only an inconvenience for me.

Apparently there are plenty of ISO images of the XP disc out there, without the installation files of course.  If you can boot off of a disc you make with those files from your second computer, it should only take a second to restore your OS.  Here's a site I found explaining the procedure: [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/).

Sorry, I didn't look for an ISO of XP, but it should be easy to find on google.  Good luck, my friend!

Edit: I don't think you will be able to fix the MBR from within Linux.  I think you have to boot off of the CD.  I don't know that, but I'm pretty sure...


Thank you so much for your followup.  I can't get Ubuntu to respond to a cd.  Instead, I'm pouring over some info I got off of this site about Ubuntu.  I'm hoping that if I read enough, I'll be able to get a handle on the Terminal feature and eventually plug in the right code to get to what I need.  I'm really not even certain that Ubuntu overwritten my MBR - I've been assuming it has because I can't access diddly.     I do hope you get some help on your issue.   Take care.

---

### Post by lulabelf on 2010-05-01
> **oldfred said:**
> When you installed did you put grub2 into the windows partition?

Windows has a two part boot. All computers start boot from the MBR of the primary master hard drive. IF SATA drives you set primary master in BIOS. Windows boot in MBR starts a second part boot from the PBR or partition boot record or boot sector. Grub also uses that second part to boot windows from grub. Grub normally does not install to a PBR but can be. So if you installed grub to the windows PBR you overwrote the second part of the windows boot loader.

You can repair that with these instructions from Ubuntu or windows repair disk.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows. You would only need to run fixboot command.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)


Hello!  I'm so thoroughly confused at this point that I'm not sure what I did!  I installed 9.10 from a cd; not sure if it went to GRUB2.   I'll check out the references you sent and see what happens.   Just feeling really defeated - but not out of the running.   I've been busy trying to understand all the lingo about Ubuntu by printing out a file called 'About Ubuntu & Command Lines'.    I'm giving up for the evening and will look at things tomorrow.       Thanks for your info.

---

### Post by oldfred on 2010-05-02
If you would like to have us review you boot process this documents just about everything related to booting. We can often see if something is missing or in the wrong place. I use this myself before & after any system changes to make sure I did what I thought and to document it.
You can run from your system if you can boot into Ubuntu or from a liveCD (results.txt may save to different locations).

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by lulabelf on 2010-05-02
> **oldfred said:**
> If you would like to have us review you boot process this documents just about everything related to booting. We can often see if something is missing or in the wrong place. I use this myself before & after any system changes to make sure I did what I thought and to document it.
You can run from your system if you can boot into Ubuntu or from a liveCD (results.txt may save to different locations).

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


Thanks for your offer.  I solved my problem by updating to Ubuntu 10.04.  Also, I was directed to the Medibuntu site.  You see, I initially wanted to be able to download videos from Netflix or be able to watch them through VLC.  When I couldn't get VLC Player to work I threw my hands up!    Not thinking about going back to Windows now.  Having fun working with Terminal now that I understand it.

---

