---
title: "system crash after package loads"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by skypuppy on 2011-01-21
I loaded Ubuntu 10.10 via usb thumb drive, installed the graphics drivers from the ati web site, then had a nice, well-functioning system.  I proceeded to load all the development software, tons of system tools.  System worked fine hopefully last long time.
Next day, I loaded a lot of graphics (actually multimedia) packages, including lots of kde tools that sounded really great (I think the original windows method was gnome), then powered down. 
Today when I powered up, login took --forever--.  When a login screen finally came up, it was TEXT mode only!

So is there a "repair" method of booting off that thumb drive?  Or some other method of getting the graphics-based windowing back?  

Also, why do ALL Linux and Winblows loaders require a complete reformat of the disk drive and completely blank reload?  There are many, many programs and setups I don't want to (and probably can't) reload.  I'd like the Linux/Ubuntu upgrade (moving to newest kernel etc.) to keep the system as it is and only upgrade the kernel and appropriate other files without having to redo every dang thing on the planet every time I upgrade.  Is this possible?????

Thanks.

---

### Post by cariboo on 2011-01-21
When you install drivers from AMD/ATI's web site, every time there is a kernel update, you have to reinstall the drivers. You would be far better off installing the drives that are in the repositories by going to System-Administration->Hardware Drivers/Additional Drivers.

You may be able to boot to the desktop, by starting in recovery mode, hold down the shift key to get to the grub menu, if it doesn't show automatically, and use the arrow keys to select recovery mode, at the menu select failsafe-X and you should boot to the desktop, where you can install the proper drivers.

> So is there a "repair" method of booting off that thumb drive? Or some other method of getting the graphics-based windowing back? 

Just boot to the desktop with your Live USB device, you can then make any repairs needed.

> Also, why do ALL Linux and Winblows loaders require a complete reformat of the disk drive and completely blank reload? There are many, many programs and setups I don't want to (and probably can't) reload. I'd like the Linux/Ubuntu upgrade (moving to newest kernel etc.) to keep the system as it is and only upgrade the kernel and appropriate other files without having to redo every dang thing on the planet every time I upgrade. Is this possible?????

You don't need to do a reformat to re-install grub, and there should be a repair function available on your Windows boot disk. I would go into how to repair Windows here, as this is an Ubuntu support forum. To re-install grub, boot from your Live USB device, and once at the desktop, open an Applications->Accessories->Terminal and type:

```
sudo fdisk -l
```

The above command will give you a listing of all your partitions, take note of which one contains Ubuntu, Next in the same terminal type the foloowing commands, pressing enter after each one:

[LIST=1]
[*]sudo mount /dev/sda1 /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

replace /dev/sda1 wth whatever partition Ubuntu is on, on your system. Once at the prompt again, type:

```
grub-install /dev/sda
```

once that command has finished, type:

```
update-grub
```

once the update-grub command has finished, press Ctrl-d twice and reboot.

---

### Post by skypuppy on 2011-01-21
This particular system has only Ubuntu 10.10 Linux on it (now.  started with 10.04.)  
During boot, Im' given ZERO options to do anything now; it simply goes to the text login after many, many minutes.

I used the thumb drive and started up 10.10 that way, but I'm only given the option of "install" and "live cd."  There is no "repair system" option that shows up.  Is there a non-documented key sequence or other method of making the days and many, many hours already invested in this setup without starting from scratch *yet again,* please?

Aside: this box is to be used for hd and sd video capture using an Intensity Pro, so I must use all 6 sata discs as a raid 5  config.  That isn't working yet either.  But it's a minor problem compared to getting the system healthy again.  Thsi is a brand new, freshly built system, built by me.   Don't worry, I've built dozens of systems before - all successful.

---

