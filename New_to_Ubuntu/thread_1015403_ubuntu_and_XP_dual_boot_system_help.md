---
title: "ubuntu and XP dual boot system help"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by pappasaa on 2008-12-18
I have ubuntu installed on one of my drives. I took that drive out of the computer and installed windows on another drive. Now i want to have both drives in the computer but with a dual boot system.

The ONLY reason I need windows is for school...its required

So i want to setup a dual boot system so I can choose the OS on startup...Any tips?

---

### Post by Kellemora on 2008-12-18
Hi P

Don't do this until one of the Guru's verifies it's correct!  You may NOT have to move the drives around as I've indicated.

Drop the Ubuntu drive in slot 1 and the Windows in drive 2 for now, it will get moved back to drive 1 later if you want it that way, boot it up.

In terminal type
```
blkid]
```
This will give you the UUID of all partitions.
You will need the UUID of your Windows drive.
Install Grub on your Ubuntu drive, if the Ubuntu installer didn't do it for you already.  It should have!  It may have even found Windows for you already too if the Windows drive was installed when you installed Ubuntu.
However, the Doze does not like to play second fiddle usually, so it sometimes needs to be the first boot device in the Grub listing.

That being said, I left the Doze on a few of my Ubuntu computers and have it set to boot into Ubuntu and the Doze boots up just fine as long as it's in drive space 1.

Once Grub is loaded, you can now switch the drives back around so the Doze is in slot 1 and ubuntu in slot 2.  You will still be able to boot Ubuntu as the default after you edit Grub to place the Windows bootloader and fix the MBR which I show how to do below.

Install a Live CD that can get you into a Root Terminal.  I use Super Grub.
In Terminal type
```
sudo grub
```
then type
```
find/boot/grub/stage1
```
You use this info to set the root device.
It will look something like root (hd0,1) or (hd1,1)
Whichever one it is for Ubuntu (where Grub is installed) type
```
setup (hd0)
``` or
```
setup (hd1)
```
now type quit.

This will place the path to the bootloader onto your Windows drive in slot 1 and point it to your Ubuntu drive where the bootloader (Grub) is installed.

The bootloader (Grub) comes up on the screen and gives you a few seconds to select Windows, if you don't, Ubuntu will boot up as the default.  If you set Grub up as Ubuntu as the default.

Been a long day, I'm tired and may have missed a step or may not have clarified how to do something well enough.  It's not hard, but the Doze is picky picky picky about some things.  

So Please wait for a guru to add clarification!

TTUL
Gary

---

### Post by Fixman on 2008-12-18
> **pappasaa said:**
> I have ubuntu installed on one of my drives. I took that drive out of the computer and installed windows on another drive. Now i want to have both drives in the computer but with a dual boot system.

The ONLY reason I need windows is for school...its required

So i want to setup a dual boot system so I can choose the OS on startup...Any tips?

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by bumanie on 2008-12-18
You can follow the apc.mag route if you wish. I don't believe Kellemora's advice will work in this situation as grub has no idea of windows existence and thus will only ouput where grub is installed for a single linux hard drive configuration. Kellemora's procedure is correct if windows has been reinstalled in a dual boot and windows has over-written the mbr.

Have the windows drive as the first bootable hard drive drive in bios and the ubuntu drive as the second bootable drive, ensuring you leave cd-rom as the first bootable device so you can boot from a live cd when needed.

Add the following to the bottom of your /boot/grub/menu.lst under this line

[COLOR="Red"]### END DEBIAN AUTOMAGIC KERNELS LIST[/COLOR]

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

To add to the /boot/grub/menu.lst > gksudo gedit /boot/grub/menu.lstThen save.

Then boot with live cd. In terminal

> sudo grub
> root (hd1,0)
> setup (hd0)
> quit
> sudo shutdown -r now

Your system will reboot and if above has been done correctly, you should have dual boot options available. 

At least that's how I would go about it if it were my own system.

Another option would be to try GAG bootloader which can boot up to 9 operating systems and does not involve any changes to lists or grub - it would work from where you at now.

---

### Post by pappasaa on 2008-12-18
i am so green to this my head is spinning just reading this...I am sorry

---

### Post by jimrz on 2008-12-18
Does your computer's "setup" utility (your initial splash screen should say something like "press f12 (or whatever) to enter setup) allow you to choose which hard drive you boot from? If so, try putting your Win drive as "drive 1" (it won't be happy anywhere else) and ubuntu as "drive  2". Then set "drive 2" as your first boot option to boot ubuntu automatically. When you want to boot Win you will need to use the "setup" utility to select "drive 1" for that session.

---

### Post by Sef on 2008-12-18
Read [Psychocats]("http://psychocats.net/ubuntu") to dual boot.

---

### Post by xjcannonx on 2008-12-19
I will second jimrz answer, it would be the easiest to do with the least headaches...

although an advantage of having two OS's on the same hd and having an extra hd could be to have all your data on a separate drive from your operating systems...

---

