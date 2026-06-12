---
title: "Intermittent Boot Problem"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Nplotnick on 2010-07-30
Having a strange issue when booting my system. BIOS loaded fine and I could then see that the HDD was trying to boot the computer. After a few seconds, the green light on my CRT turned amber and no login screen appeared. I reset the computer a few times and then the bootup when normally. After I shutdown the computer, the issue happened again. 

I am running the latest version 10.04 of Ubuntu and the system has been fine for about 3 months since I first build it. There is a new 320GB WD Caviar Blue SATA drive and an NEC DVD drive. The MB is a stock Intel MB with a 1GB and 256MB memory installed. I am using the onboard audio, video and network controller. 

Thanks!

Neil P

---

### Post by QIII on 2010-07-30
I suspect this is on the hardware end.

Can you recreate the problem with the LiveCD in the drive?

---

### Post by S.R on 2010-07-30
I am throwing my dart at the MB ... either cracked or just gone bad.

Wouldn't this be a good time for the Power Supply to sneak in some problems though. Do you have a voltage/ohm meter?

I tempted to throw another dart at the HDD have some bad sectors.

---

### Post by Nplotnick on 2010-07-31
The system seems to boot fine with the 9.10 DVD that I have. (Disk came with the SAMS book Ubuntu Unleashed. I have not yet gotten the 10.04 disk in the mail that I registered for)

Same thing happened again this afternoon. The system went dark after trying to boot. Once I hit the reset switch, all returned to normal.

---

### Post by Nplotnick on 2010-07-31
I too suspect something with the HDD. The disk manager utility does not allow me to check the file system on the hard drive since it is in use. Is there something similar to Windows Disk Scan that I can use on a mounted drive to verify the file system from a boot drive or must I run such a utility from a Live CD?

---

### Post by oldfred on 2010-07-31
My monitor went to sleep on both the liveCD and first boot. The nomodeset works for some other than just nvidia, but others have different settings.

To see what video you are using from liveCD if you can get into it:
lspci | grep VGA

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO on USB, or in USB's syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by Nplotnick on 2010-07-31
Running from the 9.10 Live DVD, I ran the Palimpset Disk Utility on the HDD. The SMART status always shows the disk as healthy. The file system check passed. I also ran a disk self test (short for less than 10 minutes) and that also passed.

I imagine that these tests just verify the integrity of the disk but do NOT check that any particular file is corrupt. This system has been used from about 4 months as my LINUX test bed. I do not think that the MB or RAM is bad. The HDD is brand new and installed about 6 weeks ago when I settled on the Unbuntu distribution for the system.

I think that I need to have the system verify or reinstall the OS files. I want to make sure that I do NOT have to install 9.10 and THEN install 10.04 as this will take some time. I also want to make sure that I can keep all the stuff I have been using on the system. 

Thanks again!

Neil P

---

### Post by Nplotnick on 2010-08-02
Using the instructions from the post "repair your broken ubuntu using livecd" Below is the link with the details.

[http://ubuntuforums.org/archive/index.php/t-422523.html](http://ubuntuforums.org/archive/index.php/t-422523.html)

I followed the exact instructions after booting with my version 9.10 DVD. After the reboot, everything was back to normal. Booting is fine and I lost NONE of my files or settings.

N.P.

---

