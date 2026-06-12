---
title: "Error Message at installation try"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Miss Kitty on 2009-06-06
[FONT=Times New Roman][SIZE=2]My son was given an HP Pavilion 7840, which has a Celeron 766 Mhz processor, a 30 gig Hard drive, and I installed 512 megs memory (all allowed). The hard drive contains Windows XP, which is locked up with a password, and F8 at bootup did not give me a menu screen to choose Safe Mode, to allow changing or removal of the password. The previous owner refused to give the password, saying you will just have to reformat the hard drive to use it. Instead of a boot menu, I just got HP's blue screen and Welcome to Windows XP, with owner name and password blanks. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]I made an MS-DOS startup diskette from my computer, but the HP did not recognize the floppy. I then tried putting the Ubuntu 8.10 CD (downloaded and burned to CD from the Ubuntu website) in the CD drive, and tried to boot. I had checked the BIOS previously, and order of booting is 1, removable devices, 2, CD-ROM drive, 3, hard drive.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]On restarting the system with the installation CD in, I got the Ubuntu logo, and then the menu, from which I chose "Install Ubuntu". After quite some time with a colored progress bar going across the screen, the screen changed to read "[     0.000000]ACPI: no DMI BIOS year, acpi=force required to enable ACPI[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Loading, please wait .........[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][1004.455794] SQUASHFS error: sb_bread failed reading block 0xd5b6[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][1004.455883] SQUASHFS error: unable to read fragment cache block [3562ef7][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][1004.455907] SQUASHFS error: unable to read page, block 3562ef7, size aaea[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]   *Reloading system log daemon..........[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]   *Reloading system log daemom.........                                                                                __[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2](That last of the line being where the cursor ended up)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]I waited, and waited, and waited. Nothing else happened. After several hours, I just turned the unit off. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]What does the above mean?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]Question 2, if question 1 can be resolved, is, how do I get past HP's proprietary boot action to be able to boot into safe mode?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]Thank you![/SIZE][/FONT]

---

### Post by presence1960 on 2009-06-07
I looked on HP's site and that computer did not come with XP, it came with 98 or ME. So there is no hidden recovery partition to recover Windows. You must have a legitimate Windows install disk.

I would try burning another Ubuntu disk at the slowest speed possible. try doing this to burn the CD : [https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html) 

I would change the order of booting in BIOS to 1. CD  2. Hard drive  3. removable devices. Then try booting off the Live CD. When the menu comes up choose "Check CD for Defects". If all is ok use "Try Ubuntu without any changes to your computer". you will be able to run Ubuntu off the CD, but it will be slow. This will give you an opportunity to see if everything is working on your machine under Ubuntu. This will give you a decent idea of what Ubuntu is like except for speed.

If you can't get the password for Windows or don't have a legit Windows install disk I would install Ubuntu using entire disk. This will use the whole hard drive for Ubuntu, effectively wiping everything off the disk.

If you still get those ACPI errors you may want to look at this to try different booting options : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Scroll down to the area that deals with pressing F6. This is what you may need to do if those errors repeat again.

---

### Post by QIII on 2009-06-07
Not sure if you are going to be able to get around the password problem on the hard drive.

Did the previous owner at least give you the XP restore or installation disks?

With regard to the SQUASH errors, here's some info.  Check all of these possibilities.

[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)


BTW:  If that all sounds Geek to you, it probably is.  Fortunately, we are all here to teach Geek.

---

### Post by QIII on 2009-06-07
RE:  Last post by presence1960.

If the machine has Win ME installed, it is probably a waste of your time to even deal with it.  Win ME was nearly useless.

---

### Post by presence1960 on 2009-06-07
> **QIII said:**
> RE:  Last post by presence1960.

If the machine has Win ME installed, it is probably a waste of your time to even deal with it.  Win ME was nearly useless.

It was one of the biggest jokes wasn't it?

---

### Post by QIII on 2009-06-07
An abortion.

---

### Post by Miss Kitty on 2009-06-07
Thank you for the answers. I had intended to use the whole hard disk for Ubuntu. I do not have an extra legal install CD for Windows XP, and the previous owner did not include either an installation CD or a Recovery CD. Yes, this system came new with Windows ME installed, but the previous owner obviously upgraded, as the splash screen definitely said Windows XP. 
 
I am using a Windows XP Pro computer, and Roxio Easy Media Creator to burn the CDs with - none over 40x, with SmartBurn on, and overrun protection on. I will try holding the burn speed down even further, and burn a new CD.

---

### Post by woedend on 2009-06-07
Yeah, these errors are very finnicky to say the least.  While trying a different burn is a good idea, I'd also recommend redownloading the ISO if at all possible to ensure the data within is not bad somewhere.  Let us know how it turns out.

---

### Post by Miss Kitty on 2009-06-07
I find it hard to believe, that someone besides me actually remembers punch cards!

---

### Post by Jazzy_Jeff on 2009-06-07
If you still have problems with the live cd download the alternate install cd and use that. It is text based but easy to use. I have problems with the live cd's myself.

---

### Post by Miss Kitty on 2009-06-07
[FONT=Times New Roman][SIZE=3]So far: I tested the integrity of the CD. No errors found.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]The memory test is running right now. Looks like it takes quite a while. I will post results when it completes, probably tomorrow during the day. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I have a new download of the 8.10 version downloading right now - it says it has another hour and 10 minutes to go. In any case, it will be on this hard drive.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]The "No DMI BIOS year" error, with ACPI etc., showed briefly but then the CD went on loading. If the memory proves good, I will then run Ubuntu Live from the CD, as suggested, and watch for problems there.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Thanks to all of you for your suggestions! I have visited both links posted in replies, and am, as we speak, following the suggestions on the SQUASHFS error link.[/SIZE][/FONT]

---

### Post by QIII on 2009-06-07
There are a few of us gray-beards around who still are geeky enough to remember punch cards...

My Dad has been a geek since the 1940s.

---

### Post by Miss Kitty on 2009-06-07
[FONT=Times New Roman][SIZE=3]As promised, here is an update. I ran the integrity check on the CD, no errors found. I ran the memory test, no errors found. I chose to run the Live CD without changes to my computer, and Ubuntu opened. [/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]The ACPI error regarding no DMI BIOS year, loading acpi=force did reoccur, once when rebooting after the memory test, and once when restarting to run the live CD. [/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]I do have a (Phoenix) BIOS update file, but since this HP did not recognize the boot floppy, I guess I will burn the boot files plus the flash BIOS upgrade to a CD and boot from that. That should work, right?  [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]****** The live CD is now in the process of installing Ubuntu to the entire hard drive! Success at last! (Guess I'd better not count chickens, though, huh.) So, now this BIOS update, mentioned above, is beside the point, because when I downloaded it from HP's website, it asked me the operating system, and I said Windows XP, so that is the format of the flash BIOS file. There was no Linux choice at all. How do I flash the BIOS now that Ubuntu 8.10 is actually installing and Windows XP is gone?*****[/SIZE][/FONT]

---

### Post by mikechant on 2009-06-08
> How do I flash the BIOS now that Ubuntu 8.10 is actually installing and Windows XP is gone?

I'd suggest leaving the BIOS alone unless you need the update in order to run.

If you want to go ahead, what other options does the HP site give for the BIOS update file format apart from Windows XP?

Later: I saw this link on another thread:
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

It might allow you to flash the bios without windows.

---

