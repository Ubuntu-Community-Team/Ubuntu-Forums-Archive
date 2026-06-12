---
title: "ubuntu + ssd"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Engammalsko on 2011-07-06
Hi, I Can install Ubuntu 11.04 on the SSD but not boot it, I don't even have a grub menu. When I've tried to install it on the HDD it worked perfectly. 

I'm using the live CD atm. Is there anything I can do from here to make it work? Btw, I also installed Windows 7 on the SSD afterwards and I was able to boot it.

---

### Post by LowSky on 2011-07-06
Using Ubuntu on a SSD myself. Installed just fine.

---

### Post by fooman on 2011-07-06
hello,  when going through the installation process....make sure to load the bootloader to the ssd and not the hard drive!  that step comes after the partitioner.  
 then make sure your bios is set to boot from the ssd.

---

### Post by u.rusty on 2011-07-06
> **fooman said:**
> hello,  when going through the installation process....make sure to load the bootloader to the ssd and not the hard drive!  that step comes after the partitioner.  
 then make sure your bios is set to boot from the ssd.

That pretty much sums it up.

I also am running Ubuntu from a SSD. I initally had a problem getting it to boot because I had the BIOS set to the wrong drive.

---

### Post by Engammalsko on 2011-07-06
I burn a Gparted live cd so I can 100% remove my partitions, try to reinstall and try to change the bios bootup settings : )

I should install Ubuntu after Windows 7, right?

---

### Post by Perkins on 2011-07-06
Windows does not play nicely with others.  If you install it second, it will wipe out your bootloader (which you can reinstall from a liveCD.)

You may wish to follow some or all of the instructions from [http://beastie.cs.ua.edu/cs150/usb-install.html](http://beastie.cs.ua.edu/cs150/usb-install.html)

Doing so will reduce the number of writes to your SSD and significantly extend its life.

---

### Post by Engammalsko on 2011-07-06
Okay, it isn't my bios settings... This is my problem "Error: The partition couldn't be found; grub rescue> "
Or something like that and it takes me to a terminal.

I first made 3 partitions of my SSD. but wven If I only have 1 partition when installing Ubuntu it still gets the same error. Isn't there anything I can do to make grub work?

In my HDD I can access all the files on my SSD and everything looks right. It must be some grub or boot file or something lika that I can edit?

---

### Post by Perkins on 2011-07-06
Perhaps try booting up a liveCD and running update-grub.

---

### Post by Engammalsko on 2011-07-06
Be more specific... Run the Ubuntu live cd and then in a shell I shall type "sudo update-grub" ? I'll try it, but what if that doesn't work? I tell you if it works in 5 minutes.

---

### Post by Engammalsko on 2011-07-06
```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.

```

Any other solutions?

---

### Post by Perkins on 2011-07-07
Two things just occurred to me:

1:  When installing to flash thumb drives, using EXT4 results in data loss and corrupted files.  Although it usually runs for a while first.  Using EXT3 would avoid this.

2:  (try this first)  It's quite possible that the reserved space for the bootloader at the beginning of the drive is smaller than on a standard disk.  The result of this would be that, when you get to installing GRUB, it overwrites important parts of partition/filesystem tables...  Try creating your partition leaving 100MB of unused space at the beginning of the disk and see what happens.

---

### Post by beast-usa on 2011-07-07
I have Ubuntu on one SSD and Win7 on the other.
I also installed EasyBCD 2.02, It found the Linux boot loader
automatically.

So I have the window boot loader on the window SSD
And the linux boot loaded on the Ubuntu SSD

When I boot EasyBCD askes which one.
I have Ubuntu as default with 5 seconds to choose.
(you can edit the names)
Ubuntu x64
Win7 x64

If I start Ubuntu the Linux boot loader will ask again which one.
If you installed Win 7 first, if you install Ubuntu first it won't ask.

---

### Post by cwmoser on 2011-07-08
I think you have to make the boot partition Active - set it using Fdisk.

Carl

---

### Post by Perkins on 2011-07-08
> **cwmoser said:**
> I think you have to make the boot partition Active - set it using Fdisk.

Carl


It can't hurt, but I haven't seen a system where it actually mattered in years.  GRUB doesn't care if the bootable flag is set or not.

---

