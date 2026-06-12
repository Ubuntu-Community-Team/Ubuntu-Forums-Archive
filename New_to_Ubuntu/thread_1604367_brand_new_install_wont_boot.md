---
title: "brand new install wont boot"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by dbowlin17 on 2010-10-23
says that i need to load the kernel first. this is a brand new install of 10.10. I am really confused and have no idea what to do. I have tried clearing the entire hard drive and reinstalling 3 times... how can i fix this???:(

---

### Post by drs305 on 2010-10-23
Something is wrong with the Grub installation or the kernel installation. 

You have three options, the first two after booting the LiveCD. 

You can post the content of RESULTS.txt, which you get by running the boot info script found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
We can take a look and make some recommendations, which may include one of the following.

You can boot and purge/reinstall grub:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

You can try to boot from the Grub prompt, which is where you are being left when the boot fails:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by oldfred on 2010-10-24
Sometimes BIOS can cause issues. Please check that none of these apply to you.

Some issues on booting install:
Bad write on CD - check md5sum, write at slowest speed, Use USB to install
CD or USB not written as bootable, just copied, DVD or RW (not just R only) sometimes an issue
BIOS settings need USB mouse & keyboard
BIOS should be set for IDE compatibility mode

[http://ubuntuforums.org/showthread.php?t=1586658&page=4](http://ubuntuforums.org/showthread.php?t=1586658&page=4)
The BIOS mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision ( or maybe just setting defaults back again)
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Asus BIOS blocked the boot from the second drive
Raid meta data on drive - even if one drive (Vendor happend to set it on)

Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
BIOS complaints about "Non-System disk or disk error"
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.

BIOS & disable "Boot Sector Virus Protection"
Antivirus was installed (Avira) and it blocked the new kernel from accessing my home folder!

---

### Post by dbowlin17 on 2010-10-24
Thank you both for your quick responses. I decided since the 2 disks that I had tried installing from were made with my laptop, I would try using my 9.10 install disk. If this still doesn't work, or if when I update all the way to 10.10, it doesn't work I will then try running boot info script. I haven't changed any BIOS setting since my computer last worked. I have used ubuntu since 9.04, but not really had any problems until one day I came home and it wouldn't boot, then i couldn't boot into live cd cause my 2nd ide port failed. then my computer won't boot off usb. so long story short I went for a new install and that didn't work either... hopefully the install of 9.10 will, and then upgrading to 10.10

---

### Post by dbowlin17 on 2010-10-24
fresh install of 9.10 wouldn't do it either. i restored all the bios settings to their default and that didn't help either. I wiped the bios. that didn't help either. I only have IDE ports on this computer. its a socket 478 P4 with RIMM. I have tried reinstalling grub. I will post the results.txt file next. Once it loads into a live cd and everything, I will log in there and copy and paste it.

---

### Post by dbowlin17 on 2010-10-24
UPDATE: Booted into 10.04 alpha 3 disk i had laying around. it told me that my hard drive had bad sectors. So i booted into ultimate boot cd. then i ran a hard drive test and got errors. so hopefully this all was a bad hard drive. its still under warranty so i am shipping it out tomorrow. if the problem still persists with a new drive i will update. thanks for the help!

---

