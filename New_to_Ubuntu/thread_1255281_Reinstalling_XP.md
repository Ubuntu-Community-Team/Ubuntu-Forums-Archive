---
title: "Reinstalling XP"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by winjeel on 2009-09-01
I've got both Ubuntu and XP on my computer. Please don't tell me I don't need XP, it runs LightRoom and other programs I need. At the same time Ubuntu is the reliable side that I wake up to, along with my morning coffee when I start work in the morning.

I am happy with Ubuntu (9.04) and want to keep it completely untouched, but may need to reinstall XP (and all related programs). It's got slow, really slow, and less reliable than what it was when I first got it. It can't defrag' properly now, CC Cleaner can only do so much, and removing unused programs doesn't help much. Half way through a LightRoom slide show it just blue-screened and rebooted... completely out of the blue (why 'blue'?)

So, if I go to reinstall XP might my Ubuntu be in danger? Is there some secret mysterious code in the Dell Windows XP clean install CD that might do away with the whole lot? (please note, I'm posting this in the "*Absolute* Beginner Talk" forums for a reason) :)

Thanks in advance for your help. :)

---

### Post by halitech on 2009-09-01
if you already have an XP partition then you should be able to reinstall to the same location without harming your Ubuntu install as long as your cd isn't a recovery cd. The only thing you will need to do is restore grub afterwards as windows will write its boot loader to the MBR preventing Ubuntu from loading but its easy to fix.

---

### Post by mdmarmer on 2009-09-01
Make a good backup first.
If you reinstall from a recovery disk, these disks almost always start by formatting your hard drive.
After that is all done you would need to shrink the Windows partition with gparted, reinstall Ubuntu, and copy your data from your backup.  It is also possible to copy your entire Ubuntu install back to the new partition(s) you create for it after shrinking your Windows install.  Then you would not need to reinstall Ubuntu -- you would just need to set up the Master Boot Record (MBR) to use Grub and boot both Ubuntu and Windows -- or you could set up the Windows boot loader to boot Ubuntu and Windows.

Mike

---

### Post by winjeel on 2009-09-01
Arr... you used a keyword "Recovery CD". I think that might be the sort that I have. If it all went pear-shaped (horribly wrong), would the partition be removed and Ubuntu lost?

What is "Grub"? And what do I do with Grub?

---

### Post by Bucky Ball on 2009-09-01
> **halitech said:**
> if you already have an XP partition then you should be able to reinstall to the same location without harming your Ubuntu install as long as your cd isn't a recovery cd. The only thing you will need to do is restore grub afterwards as windows will write its boot loader to the MBR preventing Ubuntu from loading but its easy to fix.

+1

All there is to it, but be careful. You will see your current install there when you go to reinstall XP. Just delete that and go again (you may just be able to install XP without deleting and creating the partition first). If you have personal data on that same partition it will of course be lost so back that up before you do it (including bookmarks, email addresses etc.) :)

---

### Post by halitech on 2009-09-01
if it is a recovery cd then it will restore the system to the way it was when it left the store

grub is the boot loader that Ubuntu uses by default (there are others like LILO but they do the same thing) and it tells the hardware basically what to do on start up

---

### Post by winjeel on 2009-09-01
Thanks for the info. :)

---

### Post by matsuzine on 2009-09-01
I have an emachines recovery cd that removes all partitions and that would wipe out your ubuntu.  I have a toshiba recovery cd that gives you options about where to install (which is unusual).  Most recovery cds I've used will not spare your ubuntu install, so it won't be as easy as just reinstalling to your windows partition and restoring grub.  

You could try this:

-- backup all data you don't want to lose
-- If your ubuntu install is less than 4 GB you could use remastersys to remaster your entire installation to a live cd.  That way, you can boot to your custom live cd and reinstall your system exactly as it is now!

-- boot your recovery cd
**CAREFUL:  some cds simply prompt you if you want to start recovery which will wipe out all the data on your drive and reinstall windows.  If you say yes, it will just launch into the automated install, no other options.  So don't say yes unless you're sure you want to reinstall windows.

-- see if it gives you a prompt as to where you want to install
       ..if not, the installation of windows will eliminate your linux installation
       ..if so, choose your windows partition and you should be ready to go

---

### Post by marshmallow1304 on 2009-09-01
> **matsuzine said:**
> If your ubuntu install is less than 4 GB you could use remastersys to remaster your entire installation to a live cd.

Why less than 4 GB?

---

### Post by LewRockwell on 2009-09-01
just read today where even the Windows 7 install disks refuse to do anything except/until a complete hard drive erase and reformat has been done

windoze...hahaha

.

---

### Post by Bucky Ball on 2009-09-01
They continue to put people off with their tactics in my experience.

---

### Post by Keen101 on 2009-09-01
Most likely it's gonna blow your ubuntu partition out of the water.

But, in the event it doesent, it will for sure overwrite GRUB bootloader with the windows bootloader. In that case you will need to restore GRUB.

I recommend the SUPER GRUB DISC. It works miracles!!!!

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by PaulReaver on 2009-09-01
the program you want is remastersys

it's a distro spinning program you can make a backup of your complete ubuntu install and burn it to dvd.
make sure to back up your important files to a dvd or external hard disk just in case.

then you can restore your xp to the hard disk (wiping your hard disk)
then restore your ubuntu using your remasterd ubuntu install disk with all your programs allready installed.

[URL="http://www.remastersys.klikit-linux.com/ubuntu.html"]
http://www.remastersys.klikit-linux.com/ubuntu.html
[/URL]

---

### Post by matsuzine on 2009-09-01
4 GB approx, I guess.  Because remastersys can create a live cd image, but it would need to fit onto a dvd (can't span live cd volumes).  It's really easy to use, one of the most fun things I've ever done with linux was once I started remastering.  Having an installable live cd of your preferred setup is pretty useful!

---

### Post by PaulReaver on 2009-09-01
yep but 
i remastered my ubuntu install with gnome kubuntu-desktop (kde) and xfce.

all the programs i could think of worth having, opera thunderbird audacity list goes on and on.
my respin only came out at 1.2Gb

the only problem is when you boot the live cd you have to press enter/return when it says boot:

---

### Post by isparkes on 2009-09-01
To put a slightly different point of view forward, why not put your XP stuff on a virtual machine? 

This is what I do with Office and AnyDVD (the only apps that I need from the Miscro$oft world - Office for occasional team editing of complex docs and AnyDVD because it's pretty useful).

This has the advantage that you can set "snapshots" on XP, and when things get too slow, just roll back to a previous snapshot.

You're going to invest the time to re-install XP, so why not do it in a way that means you'll never need to do it ever again... ;)

---

### Post by eriktheblu on 2009-09-01
Random advice:
I've had fairly good results with Virtualbox but I'm not sure if Lightbox would work for you (3D graphics don't translate well for me at least). If you're going to go this route you will need greater system resources than each OS individually requires. Another problem I can see is recovery disks are often specific to the hardware, and may not recognize the virtualized system.

Every time I've installed Windows, it has at a minimum removed my machine's association with Grub. If you have an install version of Windows rather than an image/recovery disk, you can install it without affecting your non-Windows partitions. This is a good reason to set up a /home partition to avoid loosing files and settings. An Ubuntu reinstall isn't that bad once you've done it a few times.

Multiple hard drives. Have hard drive A for Ubuntu, hard drive B for Windows. Install Windows first, the Ubuntu. If you need to reinstall Ubuntu, no problem because it can automatically recognize other OSs. If you need to reinstall Windows, unplug hard drive A. Added bonus: swap partitions on 2 disks for improved speed.

If you want to improve your Windows performance, I highly recommend [http://www.blackviper.com]("http://www.blackviper.com").

---

### Post by LewRockwell on 2009-09-01
> **eriktheblu said:**
> Random advice:
I've had fairly good results with Virtualbox but I'm not sure if Lightbox would work for you (3D graphics don't translate well for me at least). If you're going to go this route you will need greater system resources than each OS individually requires. Another problem I can see is recovery disks are often specific to the hardware, and may not recognize the virtualized system.

Every time I've installed Windows, it has at a minimum removed my machine's association with Grub. If you have an install version of Windows rather than an image/recovery disk, you can install it without affecting your non-Windows partitions. This is a good reason to set up a /home partition to avoid loosing files and settings. An Ubuntu reinstall isn't that bad once you've done it a few times.

Multiple hard drives. Have hard drive A for Ubuntu, hard drive B for Windows. Install Windows first, the Ubuntu. If you need to reinstall Ubuntu, no problem because it can automatically recognize other OSs. If you need to reinstall Windows, unplug hard drive A. Added bonus: swap partitions on 2 disks for improved speed.

If you want to improve your Windows performance, I highly recommend [http://www.blackviper.com]("http://www.blackviper.com").

+ 1,000,000,000,000,000 for BLACK VIPER!

.

---

### Post by egalvan on 2009-09-01
> **winjeel said:**
> 
 Half way through a LightRoom slide show it just blue-screened and rebooted... completely out of the blue (why 'blue'?)[/qoute]

Blue is easy to code in machine language.
It carried on unchanged. :)


[quote]So, if I go to reinstall XP might my Ubuntu be in danger? Is there some secret mysterious code in the Dell Windows XP clean install CD that might do away with the whole lot? (please note, I'm posting this in the "*Absolute* Beginner Talk" forums for a reason) :)


I've used several different flavors of Dell Recovery CD,
and they ALL gave me a chance to choose the type of install...
and they ALL gave a chance to choose the partition to use...
and to delete it, or keep it...


And I have NEVER seen an install/recover disk that would not give an
EXPLICIT WARNING that it was about to completely erase your drive,
and then gave a chance to exit without making any changes...

---

### Post by marshmallow1304 on 2009-09-02
> **PaulReaver said:**
> the only problem is when you boot the live cd you have to press enter/return when it says boot:

I think you should be able to get around that by doing Distcdfs, then editing the CD filesystem.  Then, you'd just go back to Remastersys and build the iso.  You can replace the bootscreen with a custom one, etc.

---

