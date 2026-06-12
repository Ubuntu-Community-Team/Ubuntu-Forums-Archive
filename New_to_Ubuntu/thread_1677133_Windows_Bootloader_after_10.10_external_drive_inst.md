---
title: "Windows Bootloader after 10.10 external drive install"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by maciej234 on 2011-01-28
I installed ubuntu 10.10 amd on an external drive. 

The drive is connected via USB.  I have windows 7 professional installed on the main drive.  When the DELL PC reboots with the external drive powered ON I get into the grub menu and I can cycle thru booting to linux and Windows 7.  HOWEVER, if the external drive is off and I reboot the PC, the windows 7 loader doesn't start and I get an error!

To give more detail, If I F12 as the system reboot and select the USB drive , I actually CANNOT boot into Ubuntu, I have to let the system boot normally.  


Is there a way I can restart into WINDOWS without having the external drive powered on?  It's not a big deal but not quite sure why my internal drive was affected with the boot process when i only installed ubuntu on the external!

---

### Post by Quackers on 2011-01-28
I suspect that grub has been installed to the mbr of your internal hard drive, rather than to the external drive.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2011-01-28
> **maciej234 said:**
> It's not a big deal but not quite sure why my internal drive was affected with the boot process when i only installed ubuntu on the external!

Actually ... it's worth you (and others) knowing that the default installation for GRUB is to the "first" hard drive it sees, and when you have an external drive and internal drive combination, the internal drive is often seen as the "first" drive.

So, you unknowingly overwrote the MBR of your internal drive when you installed Ubuntu to the external.

The script you were asked to run will show us the details ...

---

### Post by maciej234 on 2011-01-28
> **Quackers said:**
> I suspect that grub has been installed to the mbr of your internal hard drive, rather than to the external drive.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


great thanks.  I will report back later this afternoon.

---

### Post by maciej234 on 2011-01-28
> **Mark Phelps said:**
> Actually ... it's worth you (and others) knowing that the default installation for GRUB is to the "first" hard drive it sees, and when you have an external drive and internal drive combination, the internal drive is often seen as the "first" drive.

So, you unknowingly overwrote the MBR of your internal drive when you installed Ubuntu to the external.

The script you were asked to run will show us the details ...

Is it possible to have GRUB installed on the external HD and have the grub menu only show up when the external is powered on?  Also, do I need to select F12 from the startup and select the USB?  Last - i have a FW400 plug, can I boot from that?  Appreciate the responses

---

### Post by Quackers on 2011-01-28
What you want is possible. Indeed it would have been better that way, but it appears that grub may have been installed to your internal hard drive.
If you set the usb drive to boot before the internal hard drive in the bios, and restore the Windows bootloader to your internal hard drive and install grub to the mbr of your usb drive, grub will only appear if the usb drive is plugged in. If it isn't, Windows would boot normally from the internal drive.
Don't know about the firewire.

---

### Post by C.S.Cameron on 2011-01-28
You can use the Windows install DVD to run emergency repair console to fix windows mbr.

You can reinstall grub to the external using the Ubuntu Live CD.

---

### Post by maciej234 on 2011-01-28
> **C.S.Cameron said:**
> You can use the Windows install DVD to run emergency repair console to fix windows mbr.

You can reinstall grub to the external using the Ubuntu Live CD.

I was able to use the Windows DVD and repair so Windows Loads. I installed Ubunut on the external drive but it won't boot.  I've tried using the Live CD and manually install on the sdb1 drive but it still will not boot. I'd really like to be able to use the external drive.  

I was getting a GNU BASH command type prompt before I used the Windows DVD to fix MBR.  Now if I select the USB drive to boot I'm stuck at a blinking cursor and nothing loads.  

To the earlier posts-  I booted ubuntu and did an update - the update upgrade the Kernal to 2xxx.35 and after that I was pretty much unable to boot to Ubuntu because I was stuck at a black window with a command prompt!  Sorry, otherwise I would have posted those files

---

### Post by Quackers on 2011-01-28
With the usb hard drive connected please follow the request in post 2 and run the boot script.

---

### Post by victorhugo289 on 2011-01-28
So there are two parts to GRUB:

One was in your internal hard drive --Windows already repaired that, as you say.
The other piece of grub is in your USB hard drive.
The piece that was in the MBR has now been overridden by Windows.
I believe you can still boot your USB hard drive manually, because the most important part of GRUb still resides in there, as far as I know.

---

### Post by maciej234 on 2011-01-28
> **victorhugo289 said:**
> So there are two parts to GRUB:

One was in your internal hard drive --Windows already repaired that, as you say.
The other piece of grub is in your USB hard drive.
The piece that was in the MBR has now been overridden by Windows.
I believe you can still boot your USB hard drive manually, because the most important part of GRUb still resides in there, as far as I know.

I downloaded rescatux, im going to try and repair the external drive

---

### Post by maciej234 on 2011-01-29
Just an update:  I had to do a reinstall.

Anyone who wants to install Ubuntu on an external drive - follow these steps:

Select advance partition install

setup 4 partions

1. ext 4  "/"  primary, 25-50gb
2. ext 4 logical 100 mb /boot
3. logical 1gb (or double ram) swab end
4. ext 4 /home

make sure you set the bootloader to (#1)

If you boot and do a system update, it may update your kernel and after reboot you may be stuck at a black screen.

Reboot to recovery mode and low graphics mode
Install additional drivers
reboot to new kernal

---

### Post by victorhugo289 on 2011-01-29
> **maciej234 said:**
> Just an update:  I had to do a reinstall.

Anyone who wants to install Ubuntu on an external drive - follow these steps:

Select advance partition install

setup 4 partions

1. ext 4  "/"  primary, 25-50gb
2. ext 4 logical 100 mb /boot
3. logical 1gb (or double ram) swab end
4. ext 4 /home

make sure you set the bootloader to (#1)

If you boot and do a system update, it may update your kernel and after reboot you may be stuck at a black screen.

Reboot to recovery mode and low graphics mode
Install additional drivers
reboot to new kernal

Nice, to keep in mind.

---

