---
title: "Remove ubuntu"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by SANDKON on 2008-12-17
I have spent 2 months trying to get ubuntu to work on a dual boot system zith endless problems with grub, I want to get rid of ubuntu, I knoz it is cheeky asking ubuntu supporters to help but you must be aware that it is not the easiest thing to set up and if you want ubuntu to become more popular then dual booting issues esp with grub have to be sorted out. I have ubuntu on external hdd. Hoz do I restore my mbr ( don4t have xp recovery disk as was preinstalled by oem)?

---

### Post by PartisanEntity on 2008-12-17
Have you requested help on the forums to fix your issues?

The problems you are having may be easily fixed.

This might help to remove Ubuntu and restore your mbr:
[http://ubuntuforums.org/archive/index.php/t-258776.html](http://ubuntuforums.org/archive/index.php/t-258776.html)

---

### Post by ByteJuggler on 2008-12-17
Regarding restoring the Windows MBR without the Windows XP CD, see [here]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/").

I'm sorry you've had a rough time of it.  Ubuntu/Grub installs and works fine on the majority of hardware, but there are sadly problematic combinations of hardware.  This is unfortunately going to be true of any operating system, so Ubuntu is not alone in this regard.   (To wit:  I have Windows Vista installed on my main desktop, and you would not believe what grief I had to go through to get it installed originally.  The Vista installer crashes when you try to install Vista when the Intel based HDD controller on my motherboard is in RAID mode (which I do use so Intel and MS's "fix" to run in non-RAID mode was about as useful as a chocolate teapot.) Originally I had hoped this problem would be fixed by Vista SP1 but there no such luck and I believe it's still not fixed (now nearly another year later.)  I eventually got it working, but ended up having to do an enormous amount of gymnastics, e.g. installing drivers in non-raid mode, creating disk images and restoring, messing about with boot loaders, etc. to get Vista installed on my hardware config.  I just mention this to illustrate that sadly you have these types of problems regardless of OS.)  

As an aside:  Did you want to be able to disconnect your Ubuntu install/disk occassionally and keep your boot setup working regardless of whether the external disk was connected or not (was that the main problem you had?)  If so you would indeed need to be very careful about how and where you went about installing the bootloader to prevent your boot setup breaking when you disconnect the Ubuntu disk.  (Such a setup can be made to work, I'd probably suggest not putting GRUB on the internal hard disk at all, and putting Ubuntu/GRUB solely on the external disk, and then booting directly from the external disk via the BIOS boot menu or via your Windows boot.ini)

---

### Post by Captain_tux on 2008-12-17
You can create XP Recovery CDs/DVDs from within your existing XP... and if you ***really*** want, you can order them from the manufacturer (if you're still under warranty, you may not have to pay for them), but check with your manufacturer for details.

BTW, what version of Ubuntu did you try to install? 8.04? 8.10?? I personally believe 8.04 to be a lot more stable than 8.10, but like the color of my boxers, that's nothing more than a personal preference.

---

