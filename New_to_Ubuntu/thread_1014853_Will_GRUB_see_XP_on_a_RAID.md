---
title: "Will GRUB see XP on a RAID?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-12-18
I heard that Linux and GRUB dont always work well when it comes to Wintel RAIDS, so I RAID0. So I am going to physically disconnect the RAID, then put XP on a single HDD (with my data) and put Ubuntu on that too.  After which Im going to try to point GRUB to XP on the RAID0. 

So to be clear, my single Data HDD will be a dual boot(XP&Ubuntu) with GRUB on it. Neither GRUB or Linux will be on the RAID. Then I plan on pointing GRUB to XP, on the RAID, for my daily auto-Bootup. 

Will it be able to see it or is this still not stable enough for Linux/GRUB?

(If this sound like a screwy way to do it, this is my first RAID and it took me hours just to get this one up,  Im not quite ready for the Linux RAID, unless it is just a lot more sensible to do that. )

Thanks

---

### Post by caljohnsmith on 2008-12-18
I think there is a good chance you can boot XP from Grub even though XP will be in a RAID0 configuration. Are you going to boot the Linux drive on start up? I would recommend that, because if you try to install Grub to the MBR (Master Boot Record) of your XP RAID, you will likely run into problems. My suggestion would be to install Grub to the MBR of your Linux drive and set your BIOS to boot the Linux drive on start up. Once you get Linux installed, how about posting the output of the following:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sudo sh ./boot_info.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to boot XP from Grub. We can work from there if you want. :)

---

