---
title: "need to reboot to recognize my sd card"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by telltom on 2010-04-03
When i mount an sd card it is not shown. I always have to reboot and there it is. any idea?
thanks

---

### Post by ubunterooster on 2010-04-03
"not shown" in nautilus or desktop?

---

### Post by theozzlives on 2010-04-03
what kinda SD reader you using?

---

### Post by tommynz1975 on 2010-04-03
when you boot with the SD Card, have you un mounted the SD card before removing it from the reader.

Is this an internal SD card reader or one plugged into your usb?

---

### Post by telltom on 2010-04-04
This is an Acer Aspire Notebook. It has two built in slots of SD cards. I can't unmount the card because it never gets mounted. I insert the card and it doen't show on the desktop nor in Nautilus. If i insert the card, then reboot the card shows on the desktop and in Nautilus file system.

---

### Post by darkshadow on 2010-04-04
Edit /etc/default/grub and change line 9 to add pciehp.pciehp_force=1 as a boot time parameter.

Here is what it will look like edited
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

then run "sudo update-grub" and reboot.

It should start working when inserting the card after boot time.

---

### Post by telltom on 2010-04-04
thanks for the reply, but i'm a beginner and need step by step help. I know to open the termal but that's about it. I'm running Ubuntu 9.10 netbook remix.

---

### Post by darkshadow on 2010-04-04
The easiest way I can make it is to say copy and paste this in a terminal (highlight to copy then middle mouse button in terminal to paste. If you are just using the laptops touch pad both mouse buttons together counts as the third button)

sudo sed -i s/splash/splash\ pciehp.pciehp_force=1/g /etc/default/grub
sudo update-grub

Then reboot.

---

### Post by telltom on 2010-04-04
thanks, that worked just fine.

---

### Post by wilkydiney on 2010-04-11
> **darkshadow said:**
> The easiest way I can make it is to say copy and paste this in a terminal (highlight to copy then middle mouse button in terminal to paste. If you are just using the laptops touch pad both mouse buttons together counts as the third button)

sudo sed -i s/splash/splash\ pciehp.pciehp_force=1/g /etc/default/grub
sudo update-grub

Then reboot.

New  here and am reactivating this thread because I have the same problem but I do not have the grub folder

---

### Post by darkshadow on 2010-04-11
How do you not have Grub? How do you boot into Linux? What version of Ubuntu are you using?

If you are on a older version of Ubuntu with a old Grub try this command. But I don't make promises because I don't know how old this workaround is for old software.

sudo sed -i s/splash/splash\ pciehp.pciehp_force=1/g /boot/grub/menu.lst
then reboot

Note this will have to be redone if anything updates the config file. Also I am going off memory that that is the right file on older Grub versions and may be wrong.

---

### Post by wilkydiney on 2010-04-12
> **darkshadow said:**
> How do you not have Grub? How do you boot into Linux? What version of Ubuntu are you using?

If you are on a older version of Ubuntu with a old Grub try this command. But I don't make promises because I don't know how old this workaround is for old software.

sudo sed -i s/splash/splash\ pciehp.pciehp_force=1/g /boot/grub/menu.lst
then reboot

Note this will have to be redone if anything updates the config file. Also I am going off memory that that is the right file on older Grub versions and may be wrong.


Ahhh in answer to the grub I do not know

wilky@wilky-laptop:~$ sudo sed -i s/splash/splash\ pciehp.pciehp_force=1/g /etc/default/grub
[sudo] password for wilky: 
sed: can't read /etc/default/grub: No such file or directory
wilky@wilky-laptop:~$ 

OS is UserOS Extreme running Xfce on an Acer one The os is based around the Ubuntu 9.04

---

