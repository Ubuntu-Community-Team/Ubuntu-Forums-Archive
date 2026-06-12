---
title: "booting .iso file from a USB drive"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-06-27
Hi,

I have a hackintosh .iso file (iPC live DVD) but no dual layer DVD (in fact, my computer is new, and doesnt even have a DVD burner). in total the hardware equipment would cost me over $100 to burn the .iso.

So, my question is, is there any way to boot an .iso file from a USB? I know that just extracting the contents onto the USB doens't work. However, I don't exactly know how or where to install a bootloader on the USB, or how else to get it to boot. 

Can someone help me either:

(1) extract the .iso file onto a USB and make it bootable
(2) point me to a tool where i can boot something to boot directly off a .iso file (never heard of it, but would be totally cool!)

Thanks

---

### Post by Rolcol on 2009-06-27
You're not going to get support if you go the illegal route and discuss hackintosh.  If you already own a license from Apple, it may be ok but not to install on non-Apple brand computer (as stated in their terms of service).

I've had success booting off an ISO by writing the image directly onto the flash drive without extraction.  If the device is /dev/sdb, you can write the image onto the flash drive with dd.
```
sudo dd if=/location/of/the/iso/file.iso of=/dev/sdb
```

Edit:

The reason extracting the contents directly to the flash drive may not work is because the .iso has boot information.  The Ubuntu utility to create a start-up flash drive from an .iso file has to change boot flags and add information to tell the BIOS what file to boot from.

---

### Post by akimatsu123 on 2009-06-28
Thanks for your reply. To be honest, it's more for learning purposes. I don't think my hardware is even supported, so I probably won't end up installing it after all. 

Should my USB be partitioned? I currently have one fat32 partition. Should I delete the partition?

---

