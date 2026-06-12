---
title: "HD upgrade - it shouldn't be this difficult"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by ScottinSoCal on 2010-06-16
My 60 GB HDD in my work laptop is uncomfortably full, so I got a 160 GB HDD to replace it. I'm running only Ubuntu 9.10, no dual-boot stuff.

Installed new HDD in external USB carrier, plugged it into the laptop.
Booted from Partition Commander 10 CD.
Used the "Copy Disk" command to copy my old HDD to the new one.
Installed new HDD into laptop.

What I get is the rescue:grub prompt. I've found many different places that say they have the commands I need to use to restore my grub, but none of them work.

I started with "setup hd0" and got an error that setup is an unknown command.

I went into a more detailed list of commands that said to use 

- ls : No problem, I want hd0. 
- set : No problem, prefix is already hd0,1 /boot/grub. root is already hd0,1 
- search -f /vmlinuz : search is an unknown command
- ls /boot : I got a truckload of files listed.
- insmod /boot/grub/linux.mod : insmod is an unknown command

What I'm after is booting up from my new drive. For now, I reinstalled my old hdd and left the new one sitting off to the side. Little help?

Unfortunately, I left my usb boot image at home, so I don't have a way to boot into a LiveCD.

---

### Post by Chesamo on 2010-06-16
You can't copy disc information that easily. The easiest thing to do would be to ```
dd /dev/sda /dev/usb0
``` (assuming your old drive is located at sda and your new drive is located at usb0; *make sure you use the correct device names as the 'dd' command can be very destructive*) This will copy all of the block-level information from your 60GB HDD to your 160 GB HDD. Then, you will have to reboot and grow the partition to fill up the entire 160 GB. I would suggest using [RiP Linux](http://rip.7bf.de/current/) for both of these tasks.

---

### Post by cj.surrusco on 2010-06-16
I've used that process to move a file system before, it does work. You are probably just not executing the command correctly to restore the grub bootloader. 

You need an actual live cd though, I don't think you are able to reinstall grub from the rescue line.

And I'm assuming you are using grub legacy and not grub2, since you are using Ubuntu 9?

---

### Post by Chesamo on 2010-06-16
> **cj.surrusco said:**
> And I'm assuming you are using grub legacy and not grub2, since you are using Ubuntu 9?
9.10 uses GRUB2 by default, not Legacy.

---

### Post by alphacrucis2 on 2010-06-16
> **ScottinSoCal said:**
> My 60 GB HDD in my work laptop is uncomfortably full, so I got a 160 GB HDD to replace it. I'm running only Ubuntu 9.10, no dual-boot stuff.

Installed new HDD in external USB carrier, plugged it into the laptop.
Booted from Partition Commander 10 CD.
Used the "Copy Disk" command to copy my old HDD to the new one.
Installed new HDD into laptop.

What I get is the rescue:grub prompt. I've found many different places that say they have the commands I need to use to restore my grub, but none of them work.

I started with "setup hd0" and got an error that setup is an unknown command.

I went into a more detailed list of commands that said to use 

- ls : No problem, I want hd0. 
- set : No problem, prefix is already hd0,1 /boot/grub. root is already hd0,1 
- search -f /vmlinuz : search is an unknown command
- ls /boot : I got a truckload of files listed.
- insmod /boot/grub/linux.mod : insmod is an unknown command

What I'm after is booting up from my new drive. For now, I reinstalled my old hdd and left the new one sitting off to the side. Little help?

Unfortunately, I left my usb boot image at home, so I don't have a way to boot into a LiveCD.

The UUID's in the grub config probably don't match the partition UUID's of the new disk (depending on what your Partitition Commander prog actually does). Might be possible to chroot into it from a live CD and fix it up just by running sudo update-grub

---

### Post by ScottinSoCal on 2010-06-16
> **alphacrucis2 said:**
> The UUID's in the grub config probably don't match the partition UUID's of the new disk (depending on what your Partitition Commander prog actually does). Might be possible to chroot into it from a live CD and fix it up just by running sudo update-grub

OK, I'll try this, and if it doesn't work, I'll try the dd command up above. I'd really prefer to avoid having to copy all my data over again, if I can.

---

