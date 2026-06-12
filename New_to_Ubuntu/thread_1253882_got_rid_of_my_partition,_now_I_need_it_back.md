---
title: "got rid of my partition, now I need it back"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Rrory on 2009-08-30
After Windows XP crashed, I got rid of my partition, so my Sony Vaio laptop is a blissful Ubuntu only environment.

Unfortunately, I still need to run a few XP programs (I checked here first to see if there was a Linux version or I could use wine. Cant blast..) so how do I partition my hardrive with Ubuntu 9.04 already installed?

Is this really hard?  Arrg.
thanks
Rory

---

### Post by credobyte on 2009-08-30
Boot from the LiveCD and use gparted ( partition editor @ System / Administration ).

---

### Post by halitech on 2009-08-30
pretty good steps here on installing windows after Ubuntu (go down about half way)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
```
Installing Windows After Ubuntu

Normally when Windows is installed after Ubuntu the master boot record will be overwritten. This means that you would have to boot off a LiveCD and re-install grub. However, here is an alternative method:

   1. Create an NTFS partition for windows (using fdisk or whatever tool you are familiar with)
   2.

      Backup the boot sector e.g. dd if=/dev/hda of=/mbr.bin bs=512 count=1
   3. Install windows
   4. Boot into a LiveCD
   5. Mount your root partition in the LiveCD
   6.

      Restore the boot sector e.g. dd if=/media/hda/mbr.bin of=/dev/hda bs=512 count=1
   7. Restart and Ubuntu will boot
   8. Setup grub to boot windows 
```

---

### Post by Rrory on 2009-08-30
I actually had my hard drive partitiond by someone else, so I am not familiar with the fdisc or have a tool. Can I get an fdisc somewhere?

That's a great link.
thaks a lot
Rory

---

### Post by halitech on 2009-08-30
the live cd has Partition Editor included

---

### Post by mystmaiden on 2009-08-30
You might try running windows as a guest host in virtualbox..

---

### Post by Rrory on 2009-08-30
wait do you mean my  cd for Hardy Heron? I've upgraded by downloading to 9.04. I don't have a CD of 9.04.

but I'll do it. So if I put Hardy Heron in my drive, the partition editor will pop up again? which do I choose? live install or what.

thanks for the help
Rory

---

### Post by halitech on 2009-08-30
whichever live cd you have will work

when you boot from the cd, select the option to try without installing

---

### Post by magicmax0 on 2009-08-30
simply install gparted from the repositories. Use Synaptic. Then its available under System > Admin > Partition Editor.

---

### Post by halitech on 2009-08-30
> **magicmax0 said:**
> simply install gparted from the repositories. Use Synaptic. Then its available under System > Admin > Partition Editor.

if only it was that simply. You can't modify a mounted partition so running it from an install won't work

---

### Post by Rrory on 2009-09-03
wow I burned the CD for 9.04 and successfully installed it. Now the partition editor came up, and my old partition; 73.1 GB Ubuntu  and
 windows 1.4 GB was too small for windows.

I chose 'specify partitions manually' but I'm stuck on what is reasonable. I just plan to use windows for a few programs for work and websurf etc in Ubuntu. So I need help on the values of gigabytes to resize to.

 how much for sda1 ext 3 [ubuntu] and how much for sda5 {linux swap} [windows]

My laptop is an old Sony VAIO S-360 with 512 RAM (Pentium 735. 1.7 GHz)
   
Ubuntu has been so easy; I never dreamed I'd be doing this myself. It's fantastic and now my Dad wants to have me install Jackalope for him! And my sister...
                           thanks
                               Rory

---

### Post by halitech on 2009-09-04
you will probably want to give windows about 8-10 gigs of space and the rest for Ubuntu. You will need to use the Live cd in order to resize if Ubuntu is already installed as you can't modify a mounted partition.

---

### Post by Rrory on 2009-09-06
I'm resizing my partitions, and I'm asked to specify a 'root file system'.

hmm when I go back I have two partitions:
  Sda1- 46.6 GB   (will be ubuntu)
  Sda5   27,9 (boot)  [will be windows]

[urg do I need a 3rd to be a swap partition?]
and I'm asked 'mount point'. Should i choose : / or /boot to make a root file system. If not how do I do that, am a bit confused..

thanks
 Rory

---

### Post by halitech on 2009-09-06
yes you will need a swap partition. the / (root) partition only needs about 8-10 gigs, swap about the same as your ram and the rest for /home.

---

### Post by Rrory on 2009-09-06
oh thanks, okay I've done all that; resized, installed, now updating.
 
So when/how do I install windows? I read the link you gave me adn I'm confused. Do I need to copy to disc the current installation, some code?

Sorry to be such a bother. The directions are explicit, but not obvious to a newbie.
Rory

---

