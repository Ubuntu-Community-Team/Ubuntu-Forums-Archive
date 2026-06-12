---
title: "Boot failed using USB drive"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by curiousnoob on 2010-05-02
I'm trying to boot from a USB drive instead of a Live CD but keep getting the line "Boot failed".  
I've checked that the USB is the first option in the BIOS and have tried using the built in USB creation tool in Linux as well as installing directly to the USB using a Live disc.  
I always get the same error message. 
Any help would be greatly appreciated.

---

### Post by undecim on 2010-05-02
How old is your computer? It may not support booting from USB.

---

### Post by curiousnoob on 2010-05-02
> **undecim said:**
> How old is your computer? It may not support booting from USB.

Only a few years.  It definitely can boot from a USB because the option exists in the BIOS.  It is set to Enabled.

---

### Post by undecim on 2010-05-02
Can you test it on another computer or with another USB drive to make sure it isn't just the USB drive?

---

### Post by curiousnoob on 2010-05-02
Unfortunately I don't have access to another PC but I've never had any issues with the drive before.  It is a new 4GB Sandisk.

---

### Post by curiousnoob on 2010-05-03
I hate being one of those people but Bump?

---

### Post by quadproc on 2010-05-03
> **curiousnoob said:**
> I'm trying to boot from a USB drive instead of a Live CD but keep getting the line "Boot failed".  
I've checked that the USB is the first option in the BIOS and have tried using the built in USB creation tool in Linux as well as installing directly to the USB using a Live disc.  
I always get the same error message. 
Any help would be greatly appreciated.
The fact that you get "boot failed" suggests that your system is trying to execute the boot code from the USB drive but that something is not right with it.

Do you have the boot flag set?
Which boot loader (e.g., grub, grub2, other)?

There is a small chance that your BIOS is buggy and cannot correctly do the boot.  I learned that my BIOS is somewhat buggy and I have to work around its idiosynchracies by pressing F8 during boot time; this gets me to a menu screen where I can select the boot source, and then it works OK.

quadproc

---

### Post by SweetShadow on 2010-05-03
Most of the times i got this error was due to the FS on the usb thumbdrive.I always use unetbootin for this kind of stuff and thumb has to be formatted as FAT not ntfs.give it a try

---

### Post by spydeyrch on 2010-05-03
> **SweetShadow said:**
> Most of the times i got this error was due to the FS on the usb thumbdrive.I always use unetbootin for this kind of stuff and thumb has to be formatted as FAT not ntfs.give it a try

I was going to say the exact same thing. Try the linux version of UNetBootin. Make sure to mark the execute as program box under the permissions tab when you select properties on the unetbootin file or else it won't run. Try to use the built-in partitioner in ubuntu to re-format your flash drive then use unetbootin.

Good luck.

-Spydey :KS

---

### Post by techunit on 2010-05-03
I would recommend the instructions here [U][http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[/U]They have always worked for me. If you are running only Linux I think there are instructions for doing it from The Live CD as well but if you have access to a Windows PC then use this link

---

### Post by alexanda on 2010-05-03
Make sure Legacy USB support is enabled within your BIOS.

Try to manually select the boot device during post. (different on every bios, could be F2, F8, F12, 0 zero, etc)

Check to see if your BIOS needs updating.

If none of that works:
Which operating systems do you currently have access to (either installed on HD or bootable on Live CD)?

Which version of Ubunutu are you trying to install?

---

### Post by curiousnoob on 2010-05-03
> **quadproc said:**
> The fact that you get "boot failed" suggests that your system is trying to execute the boot code from the USB drive but that something is not right with it.

Do you have the boot flag set?
Which boot loader (e.g., grub, grub2, other)?

There is a small chance that your BIOS is buggy and cannot correctly do the boot.  I learned that my BIOS is somewhat buggy and I have to work around its idiosynchracies by pressing F8 during boot time; this gets me to a menu screen where I can select the boot source, and then it works OK.

quadproc

How would I check if the flag is set?  
I am not sure about the boot loader, I just tried to install directly to the drive from Ubuntu.  
I found the option in the BIOS to boot directly from the USB but the same thing happens.  
I have access to the latest 10.04 Live Disc and HDD installed 9.10 ubuntu installation but have no access to Windows or another computer.

---

