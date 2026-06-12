---
title: "BIOS Latching"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by GIFTown on 2009-05-30
So I have this old HP desktop box.  It's BIOS is pretty much up to date, featuring CD and USB booting, the like.  I have Windows XP Professional on it, and I decided to install Ubuntu.  I used a partition manager in Windows after the one on the install disk didn't work.  A few weeks after installing Ubuntu, I decided to replace it with Geexbox, a compact Linux-based media center.  I accidentally removed the Ubuntu partition and expanded the Windows one in to the unallocated space before remembering to actually go into Ubuntu and uninstall it.  So now, I have the "OS Picker" dialogue program still latched onto my BIOS, so at startup it tries to look for Ubuntu for the program for the OS Picker.  I went onto IRC #ubuntu for help, but all they told me was to go into Windows and run FIXBOOT and FIXMBR, the only problem is I can't access windows, because the OS Picker is inhibiting the BIOS checklist! SOMEONE HALP! :/

---

### Post by SunnyRabbiera on 2009-05-30
The OS picker is called GRUB, its possibly left over from your Ubuntu install.
Can your other system recognize your windows OS?

---

### Post by GIFTown on 2009-05-30
What do you mean my *other* system?

---

### Post by anchorschmidt on 2009-05-30
Boot from the Ubuntu Disk (pressing F8 or F12 at startup should help). After starting ubuntu, there should be a partitioning program under preferences/administration. If it is there then you can resize your disk. Make enough space for ubuntu and reinstall it. If you don't have the option then go to [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) using another computer and burn the image onto the disk. If you don't have an image burning program then go to [http://www.filehippo.com/download_imgburn/](http://www.filehippo.com/download_imgburn/) and burn the image using that. 

You have to reinstall Ubuntu to get to Grub to add windows (if someone knows how to do this without installing please mention it here)

So anyway after installing Ubuntu go to terminal and type in the following 

"sudo grub"
"grub> find /boot/grub/stage1"
That should return your Ubuntu partition in the form of (hdX,Y), use that:

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

(you don&#8217;t need to type the grub> bit)

Then type in 
sudo gedit /boot/grub/menu.lst

Then at the bottom of the list leave a line and type in 

title windows (Loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

* Some of this info was taken from [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) *

Then you can choose between windows and Ubuntu. You can then access your windows system and reinstall geekbox

---

### Post by GIFTown on 2009-05-30
Oh! You mean my Ubuntu installation? Windows XP did show up on the Grub.

---

### Post by anchorschmidt on 2009-05-30
Yup, but you may have to reinstall Ubuntu in order to get access to your xp partition, unless you have the XP recovery disk, so that you can 
Boot from your install CD or a floppy, choose the repair option, run recovery console, type FIXMBR and the windows bootloader will be installed.

---

### Post by GIFTown on 2009-05-30
> "grub> find /boot/grub/stage1"

after typing that, it gives me:

Error 15: File not found

---

### Post by Didius Falco on 2009-05-30
Yes, it gives you that error because you deleted Ubuntu, so there isn't a stage1 to find.

The IRC channel folks were right - what you need to do is boot with your Windows install CD and use the Recovery Console to run  FIXBOOT and FIXMBR.

After you do that, Grub will no longer be in the MBR (Main Boot Record) and it'll boot into windows by default.

Then you can install Geexbox, which will write it's own bootloader to the MBR and should pick up your Windows install and add it to the Grub menu, or whatever bootloader it uses - I'm not familiar with Geexbox.

Alternatively, you can just install Geexbox and it should overwrite the Grub menu with it's own, skipping the Windows CD step. Check the Geexbox docs for info on that.

Good Luck!!

Regards,

Didius

---

