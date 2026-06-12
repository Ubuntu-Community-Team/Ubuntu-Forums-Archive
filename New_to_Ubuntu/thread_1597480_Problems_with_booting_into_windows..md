---
title: "Problems with booting into windows."
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Uruk-hai on 2010-10-15
Ok...So I automatically made my computer boot into linux. The problem is ubuntu doesn't work when It automatically loads. It has some kind of graphics configuration error. I cant figure out how to boot into windows. I try tapping the f12 key and Stuff comes up but I'm not sure how to get into windows if I automatically get booted into an OS that doesn't work...How do I boot into windows?

---

### Post by coffeecat on 2010-10-15
> **Uruk-hai said:**
> Ok...So I automatically made my computer boot into linux.

How did you make your computer automatically boot into Ubuntu? By setting the timeout to 0 in grub? Somehow else?

---

### Post by Uruk-hai on 2010-10-15
> **coffeecat said:**
> How did you make your computer automatically boot into Ubuntu? By setting the timeout to 0 in grub? Somehow else?

Yes. there was a setting I had that made it timeout 0 seconds. It just skipped the OS screen and booted strait into linux

---

### Post by Hippytaff on 2010-10-15
There is a way to log in to command line, from there you can set the timeout to 5 or whatever by altering the /etc/default/grub file [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)
 
But I don't know how to boot to CL?

---

### Post by sikander3786 on 2010-10-15
> Yes. there was a setting I had that made it timeout 0 seconds. It just skipped the OS screen and booted strait into linux

You can either try holding down the Shift key as your computer is on the Bios screen or by pressing the up/down arrow continuously until you see the menu.

> But I don't know how to boot to CL?

By selecting recovery mode from Grub menu and then Drop to root shell or something like that.

---

### Post by coffeecat on 2010-10-15
You are giving so little information it is difficult to advise.

If you've set the timeout to zero, you've done a very unwise thing. There is a key press to reveal a hidden grub menu but it doesn't work when you've set the timeout to zero. For the record it's SHIFT with grub2 in Ubuntu 9.10 and later, and ESC for legacy grub in Ubuntu 9.04 and earlier.

The only way I know of fixing this is to boot up with the live CD, edit whatever configuration file you changed, chroot into your hard drive install to run update-grub and then reboot. Fairly easy for an experienced user; a real headache for a beginner. What do you want to do?

---

### Post by aala on 2010-10-15
Don't blame the OS for your faults!....

If your not capable of doing something, don't do it,... just don't do it; or get someone who's really capable!:mad:...

anyways](*,) **here is how you can fix it from a Live Cd!**

_______
=======
This information is from here: [[COLOR="RoyalBlue"][COLOR="Blue"]https://help.ubuntu.com/community/Grub2[/COLOR][/COLOR]]("https://help.ubuntu.com/community/Grub2")... It works 'tested'
:guitar:


METHOD - CHROOT
This method of installation uses the chroot command to gain access to the broken system's files. Once the chroot command is issued, the LiveCD treats the broken system's / as its own. Commands run in a chroot environment will affect the broken systems filesystems and not those of the LiveCD.

Boot to the LiveCD Desktop (Ubuntu 9.10 or later). Please note that the Live CD must be the same as the system you are fixing - either 32-bit or 64-bit (if not then the chroot will fail).
Open a terminal - Applications, Accessories, Terminal.
Determine your normal system partition - (the switch is a lowercase "L")
sudo fdisk -l
If you aren't sure, run
df -Th. Look for the correct disk size and ext3 or ext4 format.
Mount your normal system partition:
Substitute the correct partition: sda1, sdb5, etc.
sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
Only if you have a separate boot partition:
sdYY is the /boot partition designation (for example sdb3)
sudo mount /dev/sdYY /mnt/boot
Mount the critical virtual filesystems:
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
Chroot into your normal system device:
sudo chroot /mnt
If there is no /boot/grub/grub.cfg or it's not correct, create one using
update-grub
Reinstall GRUB 2:
Substitute the correct device - sda, sdb, etc. Do not specify a partition number.
grub-install /dev/sdX
Verify the install (use the correct device, for example sda. Do not specify a partition): sudo grub-install --recheck /dev/sdX
Exit chroot: CTRL-D on keyboard
Unmount virtual filesystems:
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
If you mounted a separate /boot partition:
sudo umount /mnt/boot
Unmount the LiveCD's /usr directory:
sudo umount /mnt/usr
Unmount last device:
sudo umount /mnt
Reboot.
sudo reboot
Post-Restoration Commands
Once the user can boot to a working system, try to determine why the system failed to boot. The following commands may prove useful in locating and/or fixing the problem.

To refresh the available devices and settings in /boot/grub/grub.cfg
sudo update-grub
To look for the bootloader location.
grub-probe -t device /boot/grub
To install GRUB 2 to the sdX partition's MBR (sda, sdb, etc.)
sudo grub-install /dev/sdX
To recheck the installation. (sda, sdb, etc.)
sudo grub-install --recheck /dev/sdX
Changing or Moving GRUB 2
The command to change the GRUB 2 installation device or boot files is grub-install run as root. This command allows the user to modify the installation by setting the ROOT directory, preload modules, run specific setup files and more. When executed, grub-install may run one or more other commands, such as grub-probe, grub-mkimage, and grub-setup. Here are some considerations when running grub-install:

The grub-install command should be used rather than grub-setup under normal circumstances. grub-setup will be called by grub-install when needed.
The command should specify a device and when executed will install the required GRUB files to the location called for in the options. (example: sudo grub-install /dev/sda )
If the user attempts to run the command with a specific partition (example: sudo grub-install /dev/sda6 ) a warning will be issued. Specifying a partition is not recommended due to the use of blocklists, which the developers consider unreliable. An option is provided on how to override this recommendation if the user still wishes to do so.
The list of options available for grub-install can be displayed in a terminal with grub-install --help.
The man page for grub-install currently does not display the all the available options.

---

### Post by aala on 2010-10-15
Although I really don't think your issue is regarded to Grub but to your graphic driver,... maybe, you were messing with the GC Drivers or something and you messed up Xorg.

anyways good luck!

---

### Post by Uruk-hai on 2010-10-15
> **Hippytaff said:**
> There is a way to log in to command line, from there you can set the timeout to 5 or whatever by altering the /etc/default/grub file [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)
 
But I don't know how to boot to CL?

That would make perfect sense if could get into ubuntu. But the problem is I cant even get it to boot. It acts all weird and askes me to change graphics configuration...If I could somehow access windows without havning to get into linux that would be ideal. Is there some way to boot up windows at startup?

---

### Post by sikander3786 on 2010-10-15
> That would make perfect sense if could get into ubuntu. 

You can boot off an Ubuntu Live CD and carry on the instructions.

---

