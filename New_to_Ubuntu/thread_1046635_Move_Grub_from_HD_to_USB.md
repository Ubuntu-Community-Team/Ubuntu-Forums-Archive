---
title: "Move Grub from HD to USB"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by syst3m on 2009-01-21
I just installed Ubuntu onto my 4gb usb flash drive, and now I'm stuck with grub on my laptops HD, instead of my flash drive. How can I move it so it is only on my flash drive, and I get my windows boot loader back?

The whole reason for installing it to a usb key was so i could take it with my and use it on other computers, not be stuck using it with only my laptop.

If there is no way to move it, how do I uninstall grub from my HD and ubuntu from mu usb?

---

### Post by mjheagle8 on 2009-01-21
[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)
uninstall grub on your computer, then edit your bios settings to boot from usb first, so you'll start in ubuntu if the usb is plugged in.

---

### Post by syst3m on 2009-01-21
> **mjheagle8 said:**
> [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)
uninstall grub on your computer, then edit your bios settings to boot from usb first, so you'll start in ubuntu if the usb is plugged in.

When I tried to boot straight from my usb, this was with grub still installed, I got an error messages saying something like "No bootable partition found.". It works when I use grub, but not when I boot straight from the usb. So wouldnt that probably still happen if I just uninstall grub?

---

### Post by mjheagle8 on 2009-01-21
what format is the usb? and is it flagged for boot?  did you make the drive bootable?

---

### Post by mjheagle8 on 2009-01-21
also, is your bios capable of booting from a usb?

---

### Post by syst3m on 2009-01-21
I am really not sure if it is flagged to be bootable or whatever. I just ran the installation and choose to use the usb instead of my HD. And yea my bios is capable from booting for usb.

---

### Post by mjheagle8 on 2009-01-21
see this link for help with installing to a usb. i dont think a simple install to the flash drive is sufficient. the link will tell you.

[http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php](http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php)

---

### Post by syst3m on 2009-01-21
So there is no way to simply move grub from the HD to the usb or just make the usb bootable?

---

### Post by mjheagle8 on 2009-01-21
no, the master boot record is what tells your hard drive what to boot from. you cant just remove that.

---

### Post by caljohnsmith on 2009-01-21
> **syst3m said:**
> So there is no way to simply move grub from the HD to the usb or just make the usb bootable?
Yes, you can install Grub to your USB drive to make it bootable, and you can restore a Windows MBR to your internal drive if you have Windows on that drive. How about first posting:
```
sudo fdisk -lu
```
And we can go from there if you want.

---

### Post by syst3m on 2009-01-21
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe30dc1d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   468408319   234204128+   7  HPFS/NTFS
/dev/sda2       468408320   488386559     9989120    7  HPFS/NTFS

Disk /dev/sdb: 4063 MB, 4063232000 bytes
255 heads, 63 sectors/track, 493 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005dfcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7470224     3735081   83  Linux
/dev/sdb2         7470225     7920044      224910    5  Extended
/dev/sdb5         7470288     7920044      224878+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2009-01-21
OK, how about doing the following to install Grub to the MBR of your USB drive:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Then to restore a Windows equivalent MBR to your sda drive, how about trying:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then reboot, set your BIOS to boot your sdb USB drive, and if all goes well you should at least get the Grub menu on start up, which is 90% of the battle. If you installed Intrepid to your USB drive, you should also be able to boot into Ubuntu, but if you installed a previous Ubuntu version, most likely your Grub's menu.lst file will need some tweaking in order to boot into Ubuntu. How about giving that a shot and let me know how far you get.

---

### Post by syst3m on 2009-01-21
It worked! Grub now only pops up when the usb is plugged in.

So does this mean that I can boot ubuntu off the usb on any computer now that grub is on the usb? Also you said 'Windows equivalent MBR' meaning I'm using lilo now instead of the windows default or grub, right? If yes, will that be over written if I were to reinstall windows at a later time?

---

### Post by caljohnsmith on 2009-01-21
> **syst3m said:**
> It worked! Grub now only pops up when the usb is plugged in.

So does this mean that I can boot ubuntu off the usb on any computer now that grub is on the usb? Also you said 'Windows equivalent MBR' meaning I'm using lilo now instead of the windows default or grub, right? If yes, will that be over written if I were to reinstall windows at a later time?
Yes, you should be able to boot your Ubuntu USB drive on other computers, assuming they support USB booting, the only thing you might have to be concerned about is how well the other computers' hardware is compatible with Ubuntu. And when I said "Windows equivalent MBR", all that means is that you have a boot loader (lilo) installed to the MBR of your sda drive that performs the exact same function as a proprietary Windows MBR. So if you reinstall Windows at some point, you'll just get a genuine honest-to-goodness proprietary Windows MBR, rather than your present lilo MBR which does the same thing. So bottom line is, it doesn't really matter since they both do the same thing. :)

---

### Post by syst3m on 2009-01-21
Well thanks for everything.

---

