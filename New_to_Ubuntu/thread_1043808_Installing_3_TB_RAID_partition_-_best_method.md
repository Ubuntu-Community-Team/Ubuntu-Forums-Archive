---
title: "Installing 3 TB RAID partition - best method"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by AndyInNYC on 2009-01-18
I know that by default, fdisk doesn't support a 3 TB drive.

Following directions which used gparted and a gpt partition (?) I got my RAID array up and running.  But upon moving the hardware to a new machine, it 'disappeared' with bad journaling or some such error.

My boot drive will be a 120 GB ATA drive (but recogized as sdX) and a 3 TB array on a 3ware 9500S-8 as sdY.

What's the best setting in either the installer (manual partitions) or to setup the array post install?

Thanks all.

Andrew

---

### Post by Bachstelze on 2009-01-18
Just format your RAID array to whichever filesystem you want and choose a mount point for it, like you would do for a single disk.

---

### Post by AndyInNYC on 2009-01-19
Thanks for your response.

My problem is one of steps and comfort <g>.

I believe that the steps I'm forced to take are:

sudo parted /dev/sda
mklabel gpt
mkpart primary 0 -0 (-0 is supposed to make sure I use all of drive)
quit
mkfs.ext3 /dev/sdx1

does this all sound correct?

Thanks

Andrew

---

### Post by Gimpy_Rob on 2009-02-23
Hey,
I'm about to try the exact same thing.  I have 4 1tb drives on a 3ware 9550SX-4

I will try your exact string of commands.  I don't know if you are still having trouble, but know that it helped me :)

I'm going with xfs instead of ext3 though... I think.  I need to look into it a bit more.

I already tried using fdisk, and starting moving over the data from the old drives (new system drives, in raid1), when I realized that it was only a 2tb partition.  Then I had to run, and I haven't been home since.

I'll report back my findings.

---

### Post by AndyInNYC on 2009-02-24
Gimpy_Rob,

We're using pretty much the same hardware/configuration.

My array has been rock solid; however, after I set up the array, I did need to initialize it (which I hadn't grasped from the manual, etc.).

Additionally, one of my Hitachi drives kept dropping out (and requiring me to start over) as I was trying to get everything set up.

It turned out that I needed to connect the drive to a SATA port on the machine and run the diagnostics CD against the drive to reset the SMART parameters and other stuff to get it to stay online.  Once I did this, I haven't (and don't expect) a hiccup.

Good luck.

---

