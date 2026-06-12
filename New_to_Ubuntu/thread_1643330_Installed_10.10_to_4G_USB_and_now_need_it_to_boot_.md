---
title: "Installed 10.10 to 4G USB and now need it to boot up my machine"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by jprobe on 2010-12-11
I installed Ubuntu 10.10 onto a 4G thumb drive so that I could boot from it without needing to use up space on my internal HDD which I have Windows 7 OS installed on.  Everything works fine with both my MS OS and Ubuntu.  GRUB2 sends me to my desired OS no problem.  But what I am having an issue with is that to get to GRUB2 I need to have my USB plugged in.  Otherwise I get this error message instead of my OS selector.  I guess that it is because the GRUB2 is installed on my USB thumb drive.  I was wanting to know if there was a way to boot my computer without needing to have my 4G flash drive plugged in.  As it is, it's like having a boot disk.  I am totally new to Linux and I have no idea what to do.  I would unistall it, but I'm afraid I won't be able to boot anything if I do.  My machine is a 64 bit Toshiba with two 2.2 gi pentium processors.  Please help.  And thank you so much.

John

---

### Post by drs305 on 2010-12-11
jprobe,

Welcome to the Ubuntu forums.

Ok, I've edited the post. If Ubuntu is only on your thumb drive, you want to keep Grub on the sdb drive and reinstall the Windows bootloader to sda.

To do this, boot to Ubuntu and install *lilo* to sda. You will get various warning messages about fully installing lilo. Don't worry about them as we aren't fully installing lilo as it supposes:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

This will allow you to boot Windows if the external is not connected, and you'll have a choice of Ubuntu or Windows if it is.


If you have problems, run the boot info script from the following link and post the contents of RESULTS.txt:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by C.S.Cameron on 2010-12-11
The lilo method sounds interesting but you should probably check out the Microsoft method before proceeding.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Edit:
Next time you install Ubuntu to USB, either disable your internal hard drive or use manual partitioning and select the USB drive for bootloader installation.

---

### Post by matt_symes on 2010-12-11
Hi

Welcome to the forums.

Just set the USB device higher than your hard drive in your BIOS and it will boot into that if it is plugged in when you start the PC. Otherwise it will boot into you internal hard drive.

BTW. Either Lilo or Microsoft's fixmbr method to work to fix your master boot record on your internal hard drive. I have used both.

Kind regards

---

### Post by jprobe on 2010-12-12
Thanks for all of the advice.  I used the lilo method, which made my machine stop requiring me to have my USB upon booting, which really takes away some of the stress associated with losing it.  I reordered my BIOS so that the USB drive was booted before the internal HDD, but whenever my machine tries to boot off of the USB I just get a flashing cursor at the top of my screen for minutes on end.  It looks like it wants to go to GRUB2, but it just flashes.  Any recommendations?

---

### Post by amjjawad on 2010-12-12
Hello John,

> **jprobe said:**
> But what I am having an issue with is that to get to GRUB2 I need to have my USB plugged in.  Otherwise I get this error message instead of my OS selector.  

If your USB is NOT plugged in, are you able to boot to Windows and login without problems?

> I guess that it is because the GRUB2 is installed on my USB thumb drive.  I 
I had done that before without any problem. When my USB HDD is plugged in, I got GRUB2 menu and choose between Windows and Ubuntu
When my USB HDD is not plugged in, I boot into Windows directly.

> was wanting to know if there was a way to boot my computer without needing to have my 4G flash drive plugged in.  J
I'm just curios, why you want to do that? :)

---

### Post by jprobe on 2010-12-12
> **amjjawad said:**
> Hello John,


If your USB is NOT plugged in, are you able to boot to Windows and login without problems?


I had done that before without any problem. When my USB HDD is plugged in, I got GRUB2 menu and choose between Windows and Ubuntu
When my USB HDD is not plugged in, I boot into Windows directly.


I'm just curios, why you want to do that? :)

I was not able to boot into windows without the USB.  I got an error message that said it couldn't find GRUB2.  With the USB I was able to run GRUB2 and choose my 7 OS. I don't want to be required to boot off of a disk in the off chance that my USB becomes damaged, or I lose it.  I would just like to have the option of running 10.10 when I plug in my USB, but otherwise be able to work with my MS OS as before.

---

### Post by amjjawad on 2010-12-12
> **jprobe said:**
> I was not able to boot into windows without the USB.  I got an error message that said it couldn't find GRUB2.  With the USB I was able to run GRUB2 and choose my 7 OS. I don't want to be required to boot off of a disk in the off chance that my USB becomes damaged, or I lose it.  I would just like to have the option of running 10.10 when I plug in my USB, but otherwise be able to work with my MS OS as before.

In that case, I'd suggest to do as drs305 suggested and post the result here and wrap up the text with "CODE" tags or "#".
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by C.S.Cameron on 2010-12-12
> **jprobe said:**
> Thanks for all of the advice.  I used the lilo method, which made my machine stop requiring me to have my USB upon booting, which really takes away some of the stress associated with losing it.  I reordered my BIOS so that the USB drive was booted before the internal HDD, but whenever my machine tries to boot off of the USB I just get a flashing cursor at the top of my screen for minutes on end.  It looks like it wants to go to GRUB2, but it just flashes.  Any recommendations?

I'm glad to hear that the lilo method worked, always nice to be able to avoid a Microsoft solution.
You should be able to reinstall grub to your pendrive, for example:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

drs305 is the master grub2 guy though.

---

### Post by drs305 on 2010-12-12
Just a quick update for those reading the thread.

*jprobe* ran the lilo commands and can now boot Windows without the thumbdrive attached.

The problem now is that with the thumbdrive inserted while booting the system ends up at a blinking cursor.

I believe this is a video issue. If the problem was with the MBR, there would be a "no system" message of some sort or it would transfer to the next drive and boot Windows. If Grub failed, there would be a "grub" or "grub rescue" prompt. 

It is likely that Grub doesn't see a second OS (not uncommon after an initial install of Grub2) and is booting without displaying the menu and the boot is failing due to video issues (blinking cursor).

I've recommended holding down the SHIFT key during boot to see if the menu displays, and if it does to press 'e' to edit the top menuentry.  Add 'nomodeset' to the end of the 'linux' line and then CTRL-x to boot. 

If it boots, *jprobe* can then go to System, Administration, Additional Drivers and add a proprietary driver for his video card.

That's where we are at the moment.

**Update:** If the above doesn't work, here is a recent post where the user states he/she has a blank screen. Could be completely blank or blinking cursor, but the solution is also posted. You might refer to this thread if the nomodeset/driver issue doesn't fix things.
[http://ubuntuforums.org/showthread.php?t=1643651]("http://ubuntuforums.org/showthread.php?t=1643651")

---

### Post by jprobe on 2011-05-01
> **jprobe said:**
> Thanks for all of the advice.  I used the lilo method, which made my machine stop requiring me to have my USB upon booting, which really takes away some of the stress associated with losing it.  I reordered my BIOS so that the USB drive was booted before the internal HDD, but whenever my machine tries to boot off of the USB I just get a flashing cursor at the top of my screen for minutes on end.  It looks like it wants to go to GRUB2, but it just flashes.  Any recommendations?

Since the method proposed by drs305 resolved the issue, I am going to mark this thread solved.  As an update to anyone who may happen to run across this:  Since the install that I did was brand new, I tallied my losses, formatted the 4G USB drive, and reinstalled 10.10 making sure that I directed the bootloader to be installed on the 4G USB partition and not my internal hard drive (which was the default option).  The install worked like a dream.  Thanks again to drs305 for all of the hard work and insight!
:KS

---

