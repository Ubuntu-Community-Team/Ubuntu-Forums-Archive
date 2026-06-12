---
title: "somehow erased /boot"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by eagle416 on 2009-11-10
So while trying to mount a really stubborn USB device (which only mounts with root from /dev/sdb) I followed online instructions too closely and formatted /dev/sda1 which happens to by my /boot partition.

I formatted it into FAT32 which bothers me, I think my boot partition should at least be ext3

I copied the /boot folder from a neighboring computer onto mine which is like a blood transfusion - it might not work because of hardware differences.

So now I'm scared to turn my computer off because I don't understand grub2 (whether it can run on its own on the MBR), and this isn't an issue of restoring /boot/grub to the MBR, this is an issue of restoring /boot

Where do I start?

---

### Post by jbrown96 on 2009-11-10
I'd try to remove grub and your current kernel, then reinstall them. That should create all the necessary files. 

1) Delete everything you copied over from the other computer. ```
sudo rm -rf /boot
``` ```
sudo mkdir /boot
``` ```
sudo chmod go+rx /boot
```

2) uninstall grub ```
sudo apt-get remove grub-pc grub-common
```
3) Remove your kernel ```
uname -r
``` uninstall that version ```
sudo apt-get remove linux-image-
``` press tab twice to get the possible options and complete with your version.
4) Reinstall the kernel, then grub. Run the commands from #2 and #3, but change remove to install. 
5) fix grub ```
sudo update-grub
```
Post back here with the status. If everything went well, then you should be able to reboot.

---

### Post by eagle416 on 2009-11-10
seemed to work, I think it installed grub-pc with the kernal. It now requires a restart. Wish me luck, if it doesn't work, I can access my files with a livecd.

---

### Post by eagle416 on 2009-11-10
I might have forgotten the update-grub bit, because I can only boot with a livecd now. I've followed the directions here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but when I type "sudo grub" it says "grub: command not found"

perhaps I should make a super grub disk and use that to boot into my native kubuntu??

---

### Post by jbrown96 on 2009-11-10
Do you get any kind of grub errors w/o the CD, or is it totally hosed? 

that forum thread won't help because it's for grub1. I haven't figured out much about grub2 either.

---

### Post by eagle416 on 2009-11-10
I get DELL and the little thing goes across the screen, and then where grub would normally appear the computer stops at a blank screen. So yeah, hosed.

---

### Post by eagle416 on 2009-11-10
Correction: Grub loads, it just gives me Error 17 and stops.

---

### Post by jbrown96 on 2009-11-11
You can try to update grub from a liveCD.

1) Boot from CD
2) Mount your /. ```
sudo mkdir /media/disk && sudo mount /dev/sdaX /media/disk && cd /media/disk
``` Change X to match the correct partition
3) try to update grub ```
sudo grub-mkconfig -o ./boot/grub/grub.cfg
```

---

### Post by eagle416 on 2009-11-11
I ran out of time/patience and ended up just backing up my home directory and doing a fresh install.

In 3 hours I was able to restore my computer to basically the way it was.

Thank you for your help anyway.

---

### Post by durand on 2009-11-11
For future reference, the reason the grub command didn't work was because Karmic uses grub2 rather than grub and it has a totally different configuration method.

---

