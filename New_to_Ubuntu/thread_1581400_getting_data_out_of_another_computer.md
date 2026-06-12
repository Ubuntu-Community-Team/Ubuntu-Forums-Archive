---
title: "getting data out of another computer"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by fantasticAesop on 2010-09-24
So, the backlight on my old Ubuntu laptop went out.

Because I am a dumb, I don't have any backups newer than six months ago.  However, as far as I know, the laptop is working perfectly fine apart from the screen showing nothing at all.

Is there some way I could get into the old laptop to copy the stuff out of it?  I have a wireless local network and the simplest "just browse the network and see if it shows up" or "connect an extra monitor and see if it shows anything" aren't working.  I don't mind using the command line or booting from my 10.04 install CD, but you're going to have to provide keyboard shortcuts because, again, I can't see a thing.

Thanks!

P.S. This machine runs Windows for the time being, since that probably makes a difference.  It has Cygwin installed too, not that I use it.

---

### Post by jtarin on 2010-09-24
Have your tried a USB connection and boot your Ubuntu Live CD in a working computer and chroot?

---

### Post by fantasticAesop on 2010-09-24
Wait, let me parse that.

USB connection?  So will any USB male-to-male cable work or will I have to scrounge a specific type?  I know I have one around somewhere, but the problem lies in the fact that I probably don't have enough money.

I can drop the liveCD into a working computer, yes.  Chroot, unfortunately, I have no idea how to perform or what I would do with it.

---

### Post by warfacegod on 2010-09-24
I'd say the simplest way would be to take the HDD out and put it into another laptop or make it a secondary drive on a desktop if you have the proper equipment.

---

### Post by fantasticAesop on 2010-09-24
I'll see about that if I have the right screwdrivers.  Leaving this open for now, though.  We'll see.

---

### Post by jtarin on 2010-09-24
> **fantasticAesop said:**
> Wait, let me parse that.

USB connection?  So will any USB male-to-male cable work or will I have to scrounge a specific type?  I know I have one around somewhere, but the problem lies in the fact that I probably don't have enough money.

I can drop the liveCD into a working computer, yes.  Chroot, unfortunately, I have no idea how to perform or what I would do with it.I would think it would work.....the transfer might be slow.
Chroot...```
CHROOT

This method of installation uses the chroot command to gain access to the broken system's files. Once the chroot command is issued, the LiveCD treats the broken system's / as its own. Commands run in a chroot environment will affect the broken systems filesystems and not those of the LiveCD.

   1.

      Boot to the LiveCD Desktop (Ubuntu 9.10 or later). Please note that the Live CD must be the same as the system you are fixing - either 32-bit or 64-bit (if not then the chroot will fail).
   2.

      Open a terminal - Applications, Accessories, Terminal.
   3. Determine your normal system partition - (the switch is a lowercase "L")

      sudo fdisk -l
          * If you aren't sure, run

            df -Th. Look for the correct disk size and ext3 or ext4 format. 
   4. Mount your normal system partition:
          * Substitute the correct partition: sda1, sdb5, etc. 

      sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
   5.

      Only if you have a separate boot partition:
          * sdYY is the /boot partition designation (for example sdb3)
          *

            sudo mount /dev/sdYY /mnt/boot 
   6. Mount the critical virtual filesystems:

      sudo mount --bind /dev  /mnt/dev
      sudo mount --bind /dev/pts  /mnt/dev/pts
      sudo mount --bind /proc /mnt/proc
      sudo mount --bind /sys  /mnt/sys
   7. Chroot into your normal system device:

      sudo chroot /mnt
```

---

### Post by jtarin on 2010-09-24
If your not sure what to mount post the results of the "fdisk -l" command.

---

