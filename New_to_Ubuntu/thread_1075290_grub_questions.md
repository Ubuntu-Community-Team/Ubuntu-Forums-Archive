---
title: "grub questions"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-02-20
I am about to install Ubuntu to a second hard disk. The first hard disk is dual booting Win Xp and Win XPPro using bootmagic.
When I install, should I first turn off the bootmagic to let it default to XPPro?
I will use manual partitioning. Should I let be grub to be installed to the first hard disk or the second hard disk when the selection comes up?
and will that make any difference?
I want to avoid a grub error to leave me scratching my head for a few hours.

---

### Post by caljohnsmith on 2009-02-20
Can you set your BIOS to boot the second HDD, the one you want to install Ubuntu to? If so, I would definitely recommend installing Grub to that HDD and leave your Windows drive untouched. You can install Grub to the Ubuntu drive by clicking the "advanced" button near the end of the installation process, and specify "/dev/sdb" (or whichever is the Ubuntu drive) as the location to install Grub to. Good luck and let me know how it goes.

---

### Post by cjv8888 on 2009-02-20
> **caljohnsmith said:**
> Can you set your BIOS to boot the second HDD, the one you want to install Ubuntu to? If so, I would definitely recommend installing Grub to that HDD and leave your Windows drive untouched. You can install Grub to the Ubuntu drive by clicking the "advanced" button near the end of the installation process, and specify "/dev/sdb" (or whichever is the Ubuntu drive) as the location to install Grub to. Good luck and let me know how it goes.

Thanks
I checked the BIOS but unfortunately there is only option for changing the boot order of 3 things:
 floppy/CDROM/Harddisk drive C
The computer came originally with an IDE cable with single connection for 1 harddisk
I changed to a new cable to connect the old harddisk as master and new harddisk as slave
So does it look like I have to install Grub to the HD0?

---

### Post by caljohnsmith on 2009-02-20
Since you only have the two HDDs, you should be fine installing Grub to the MBR of your Windows drive, or (hd0). The disadvantage of that is your drives are dependent on each other for booting, but most of the time that's not a big issue. Anyway, let me know how that goes or if you run into problems.

---

### Post by cjv8888 on 2009-02-20
Since there is both XP and XP Pro on the old drive
should I first unhide both of them using partition magic then disable the boot magic to leave it to default to one of them 
to give Grub the best chance of seeing both systems at installation?
Thanks

---

### Post by caljohnsmith on 2009-02-20
> **cjv8888 said:**
> Since there is both XP and XP Pro on the old drive
should I first unhide both of them using partition magic then disable the boot magic to leave it to default to one of them 
to give Grub the best chance of seeing both systems at installation?
Thanks
Definitely I would unhide the Windows partitions so that the Ubuntu installer will detect them and add both Windows installations to your Grub menu. I'm not sure how BootMagic works since I've never used it--does it have some boot files in one of your Windows partitions? I would definitely disable it to so it doesn't get in the way of Grub. If BootMagic uses the few free sectors that come after the MBR, that would be a disadvantage when you go to install Grub, because Grub needs those sectors for its stage1.5 file. It's possible to install Grub to the MBR without using the stage1.5 file, but then you don't get the advantage of stage1.5's error reporting for example. But probably Grub will install OK, so if any problems come up afterwards I can try to help you sort them out. Good luck and let me know how it goes.

---

### Post by cjv8888 on 2009-02-21
> **caljohnsmith said:**
> Definitely I would unhide the Windows partitions so that the Ubuntu installer will detect them and add both Windows installations to your Grub menu. I'm not sure how BootMagic works since I've never used it--does it have some boot files in one of your Windows partitions? I would definitely disable it to so it doesn't get in the way of Grub. If BootMagic uses the few free sectors that come after the MBR, that would be a disadvantage when you go to install Grub, because Grub needs those sectors for its stage1.5 file. It's possible to install Grub to the MBR without using the stage1.5 file, but then you don't get the advantage of stage1.5's error reporting for example. But probably Grub will install OK, so if any problems come up afterwards I can try to help you sort them out. Good luck and let me know how it goes.

After the above preparations and your advice, the installation went without a hitch and I can boot into all three systems .  Thanks caljohnsmith.

and now to convert wife and daughter who are Windoz addicts to Ubuntu.
Their computer is now triple booting! :D

---

### Post by caljohnsmith on 2009-02-21
Glad to hear setting up your triple-boot system went smoothly and you can now boot all three OSes; cheers and enjoy your new Ubuntu install. :)

---

