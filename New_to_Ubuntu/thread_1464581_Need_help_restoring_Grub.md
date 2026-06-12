---
title: "Need help restoring Grub"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by Omnoculus on 2010-04-28
I have been screwed by EasyBCD. 

I have a Toshiba laptop that has Windows Vista. I recently decided to  try out Linux again. I installed Ubuntu to a USB hard drive. I wasn't  touching the Vista partition at all. Vista was completely unaware of  Ubuntu. I used the BIOS setup to boot from the USB drive. There Grub had  an entry for Vista. Everything was cool. The only drawback being that  the BIOS would forget about the USB drive if it was powered down or  disconnected at any boot. But it would boot Vista from the internal  drive fine. I just want to set up a bootloader menu in Vista that would  persist even after disconnecting the drive. Well EasyBCD is not working at all. I am waiting to see if anyone can help me from that forum but I want to see if I can get help just restoring GRUB.

Now when I set the BIOS to boot from the USB drive I get  Missing operator system. 

I have booted up with the "Live CD" but I can't get grub-install to work. I can see the USB drive in Palimpsest. I can view it in File Browser but when I try:

sudo -s
grub-install /dev/sdb1

I get
grub-probe: error: cannot find a device for /boot/grub

No path or device is specified.
Try ``grub-probe --help'' for more information
Auto-detection of a filesystem module failed.
Please specify the module with the option 1--modules' explicitly.

Can anyone help?

---

### Post by bumanie on 2010-04-28
Go to point 13. h[ere]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305") - it should help as long as you are using grub 2 and not grub-legacy.

---

### Post by Omnoculus on 2010-04-28
Thanks much. I found that page and was going to peruse it more but I hadn't got that far. It made me realize I have grub 2 and not legacy.

---

### Post by sadaruwan12 on 2010-04-28
> **Omnoculus said:**
> Thanks much. I found that page and was going to peruse it more but I hadn't got that far. It made me realize I have grub 2 and not legacy.

Yes GRUB2 is very different from GRUB-legacy and be careful while editing GRUB2 it some times get screwed up.

---

