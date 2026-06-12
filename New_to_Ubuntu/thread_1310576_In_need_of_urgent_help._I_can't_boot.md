---
title: "In need of urgent help. I can't boot"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by mvalviar on 2009-11-01
I'm currenly booted on on live cd. I can't boot on my hard drive with ubuntu jaunty. I few days ago I've been getting errors from it everytime a check on my drive was performed. I just run fdisk. But yesterday another errror. I really don't know what was going on so when I saw the message "WARNING MAY CAUSE FILE SYSTEM DAMAGE" I aborted and closed the maintenance terminal. When I got to gnome performance was bad. So I rebooted. After that I wasn't able to boot. First I got GRUB read error. After that I can't even see grub. My bios can see my harddisk but. Even that livecd can't see my hard disk.

---

### Post by kansasnoob on 2009-11-01
Well that sounds like hard drive failure.

How much important data do you have on that disc?

---

### Post by g160689 on 2009-11-01
do you have sata hdd. if then try changing the cable( from sata1 to sata2 in mobo).
also try reinstalling the grub( you would find it different thread)

---

### Post by darksideforge on 2009-11-02
> **g160689 said:**
> do you have sata hdd. if then try changing the cable( from sata1 to sata2 in mobo).
also try reinstalling the grub( you would find it different thread)

Excellent advice. And if you have an IDE HDD as opposed to SATA, make sure that your IDE cable isn't bent/broken or hasn't come loose from the mobo (or hasn't backed out of the IDE connector slot in your laptop).

I lost grub once and had to completely re-install. I was able to reinstall and dual-boot and then transfer files, but it was almost a goner.  Losing grub can and does act like all sorts of hardware issues.

---

