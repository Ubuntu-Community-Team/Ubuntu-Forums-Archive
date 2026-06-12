---
title: "IDE/SATA Drives and booting.  I messed up."
date: 2010-01-29
forum: New to Ubuntu
---

### Post by ovid9 on 2010-01-29
A few months ago I built myself a new machine.  Its great, and I love it.  However, I messed a few things up which have led to me booting from my liveCD and then off my first HD.
 
Heres the issue:

My #1 Master is an 80gig IDE drive.  It was extra storage, but I want to remove it from this machine and put it in my NAS box.
 
#2 Master is my CD/DVD drive
#2 Slave is my 640gig SATA drive.
 
I'm not at my machine right now to take a screen shot of my gparted, but the IDE drive is listed as the "boot" drive.
 
I'm posting this to get an idea of what its going to entail to remove the IDE drive and get my SATA drive as a Master drive and my boot drive.   
 
Where should I begin?

---

### Post by DGortze380 on 2010-01-29
> **ovid9 said:**
> A few months ago I built myself a new machine.  Its great, and I love it.  However, I messed a few things up which have led to me booting from my liveCD and then off my first HD.
 
Heres the issue:

My #1 Master is an 80gig IDE drive.  It was extra storage, but I want to remove it from this machine and put it in my NAS box.
 
#2 Master is my CD/DVD drive
#2 Slave is my 640gig SATA drive.
 
I'm not at my machine right now to take a screen shot of my gparted, but the IDE drive is listed as the "boot" drive.
 
I'm posting this to get an idea of what its going to entail to remove the IDE drive and get my SATA drive as a Master drive and my boot drive.   
 
Where should I begin?

SATA doesn't use the Master/Slave model.

If you have a drive on a SATA channel, it is a 'master' because it's the only drive on the channel.

Just remove the 80GB drive, and install and configure GRUB on your SATA drive. Configure the BIOS to boot from the SATA drive first.

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

If you post the output of 

```

sudo fdisk -l

```

I can give you the specific commands to run.

---

### Post by audiomick on 2010-01-29
I think you will only have to switch the big HD to master and re-install.
There is a hardware switch or jumpers near the connector on the drive. Check the manual (google the drive?) for exact instructions.

edit: OK, just saw the previous post from DGortze380. Forget the mode switch... :)

---

### Post by ovid9 on 2010-01-29
Ok, thanks.  I was just going off my BIOS's showing my SATA drive as a slave.   
 
So, I unplug the IDE and go from there.  Wonderful.  
 
I'm at work now, but this will give me a great place to start when I decide to tackle this.  
 
Thanks guys.

---

### Post by ovid9 on 2010-01-30
Followed the instructions from the thread above, worked like a charm.  However, if I try it again, I'm not going to use a 6 month old version of the live CD...

Anyway, i had to run a couple more commands to setup my 2nd user account correctly again.   

The /home directory was there, but the actual user had been deleted or something, so i ran 

```
sudo adduser b 
```

and then

```
sudo passwd b 
```

back up and running like a charm.   

Thanks!

---

