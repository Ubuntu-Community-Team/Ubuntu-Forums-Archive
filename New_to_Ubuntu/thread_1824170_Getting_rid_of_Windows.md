---
title: "Getting rid of Windows"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by SoozB on 2011-08-13
Okay, I did the dual boot thing.  I love Ubuntu.  Now I want to get rid of Windows.  I read a post that said to just go through the installation process again, choosing to replace Windows.  The trouble is, when I restart my netbook (an Acer AspireOne) and press "escape" to get the boot menu, it only gives me the option of Windows 7 or Ubuntu.  It doesn't give me the option of booting from the USB stick.  

How do I get rid of Windows 7?  This netbook is new and I don't have any files in Windows 7 that I'm worried about losing, so now that I know I like Ubuntu, there's no reason to keep Windows 7 on here.

Use small words, please.  I'm fairly tech illiterate.
:)

---

### Post by Gone fishing on 2011-08-13
First install gparted ```
sudo apt-get install gparted
``` then start gparted and delete the Windows ntfs partition create a new ext4 partition in its place then install mount manager ```
sudo apt-get install mountmanager
``` and mount the new partition in say /media/storage finally update grub ```
sudo update-grub
```

---

### Post by Idefix82 on 2011-08-13
Glad you like Ubuntu so much! If you want to reinstall, then your Esc probably come too late. By that point, the bios has already decided that it will boot from the hard drive, where it then finds the menu you are talking about. You have to press some button before that. Try either F1 or F2 or F12 or Esc immediately as the computer starts. Depending on the model, there might be some picture immediately when the computer goes on, on some text about boot options. That is where you have to interrupt the normal booting routine. You have to be quick, you likely only have one or two seconds.

---

### Post by whatthefunk on 2011-08-13
> **Idefix82 said:**
> Glad you like Ubuntu so much! If you want to reinstall, then your Esc probably come too late. By that point, the bios has already decided that it will boot from the hard drive, where it then finds the menu you are talking about. You have to press some button before that. Try either F1 or F2 or F12 or Esc immediately as the computer starts. Depending on the model, there might be some picture immediately when the computer goes on, on some text about boot options. That is where you have to interrupt the normal booting routine. You have to be quick, you likely only have one or two seconds.

That was my thought.  I believe that Acer computers usually use DEL for the BIOS.  As soon as you turn on the start tapping DEL.

---

### Post by Gone fishing on 2011-08-13
The way I suggested is not reinstalling Ubuntu simply removing windows and making the space available to you existing Ubuntu.

---

### Post by walt.smith1960 on 2011-08-13
Did your netbook come with restore media, or a means to make it?  If not, I would recommend making an image of your Windows installation before removing it.  At some point in the future you may need to run software for which there is not a Linux substitute.  I use Linux 99% of the time but still have a small Windows partition.

I just had a perfect example, two actually.  I have a GPS that accepts SD cards containing POI files, music, pictures etc.  The only way to write data to that SD card in a form that the GPS will recognize is -- software from the manufacturer that only works with Windows.  

Another example.  Gigabyte MB using an Award modular BIOS.  It would **not** boot from a USB key.  That same USB key would boot fine on an older Gigabyte MB or Thinkpad laptop. In researching the problem. I read that some BIOSs will only boot from a USB stick when that stick was formatted in FAT32 with Windows.  Apparently one of the modules comes from Microsoft or something.   I formatted the drive in Win 7, installed Ubuntu with Unetbootin and sure enough, it booted right up.  It sucks that these situations exist but they do.  Don't be rash like some --  delete your Windows install then have to pay to get restoration disks or have to pay retail for Windows.  You can create an image using [Clonezilla]("http://clonezilla.org/") or another imaging program -I would create 2 in case one decided it didn't want to restore.  Now if you need Windows, you don't have to give Microsoft yet more $$.

---

### Post by Mark Phelps on 2011-08-13
Just so we know ... did you install Ubuntu using Wubi, or did you do the separate partition install?

If you don't know, next time you boot, hold down one of the SHIFT keys.  If you installed to a separate partition, that will force the display of a GRUB menu.

If you don't see that menu, you likely installed via Wubi -- and in that case, if you remove Windows, it takes Ubuntu with it.

---

### Post by goinglinux on 2011-08-13
Acer is notorious for locking the BIOS so you can't boot from USB. You may need to fix that before you can install, replacing Windows 7.

---

### Post by whatthefunk on 2011-08-13
I think we need to know more about the OPs install.  Is there a CD drive on the laptop?

---

