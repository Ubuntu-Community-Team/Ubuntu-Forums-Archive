---
title: "Running Ubuntu on a NVIDIA GeForce 8200 motherboard"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Joerice50 on 2009-01-26
Hi 

Any suggestion on getting Ubuntu 8.10 to run on this board. 

I get the following error: 
ata failed to identify ( I/O error err_mask =0x4) eventually failing to busybox with a prompt at initramfs. 

Any suggestion on how I get the Nvidia drivers into Ubuntu 8.10  before booting up Ubuntu are appreciated? 


Thanks in anticipation

Joe Rice

---

### Post by gn2 on 2009-01-26
Are you trying to boot a Live CD or an already installed system?

---

### Post by Joerice50 on 2009-01-27
The same problem occurs whether I boot ubuntu from a CD or from the installed system.

Joe Rice

---

### Post by 3rdalbum on 2009-01-27
When you go to boot up the live CD and it gives you the menu at the beginning, there's a bit where you can press one of the F keys in order to look at some alternate boot parameters. Sometimes, if your hardware isn't very Linux-compatible, you can add certain kernel parameters to get Ubuntu to boot. (press F4 or F5 or something and it tells you how to do it). Did you try these?

---

### Post by talsemgeest on 2009-01-27
> **Joerice50 said:**
> Hi 

Any suggestion on getting Ubuntu 8.10 to run on this board. 

I get the following error: 
ata failed to identify ( I/O error err_mask =0x4) eventually failing to busybox with a prompt at initramfs. 

Any suggestion on how I get the Nvidia drivers into Ubuntu 8.10  before booting up Ubuntu are appreciated? 


Thanks in anticipation

Joe Rice
How strange! I am using an Nvidia 8200 motherboard, and ubuntu works fine on it. I am using an Asus m3n78. What model motherboard are you using?

---

### Post by Joerice50 on 2009-01-28
Downloaded a further Ubuntu 8:10 AMD 64 bit version and checked the accuracy of the downloaded file via MD5Sum. Then burned another CDRom and booted the system running from the CDRom... IT BOOTS!!!! And everything works fine apart from: 

However, it wont install the partition manager cant find any drives to install ubuntu on.

Any ideas? 

I am currently moving the working Ubuntu iso into the WUBI directory to see if WUBI will install it for me I will report back tomorrow.

Joe Rice

---

### Post by Joerice50 on 2009-01-29
A false dawn I am afraid as after installing ubuntu via wubi it failed to boot cannot find the sata drives and now the CDROM also fails to load ubuntu! 

Un-installed wubi ( just in case ) and tried again to boot from the CD again, ubuntu fails to load and reports an error. 

So given that it will occasionally boot from the Cdrom ( did it twice) and I can get to the Ubuntu menu screen and edit the boot options what is the best boot string to use to make ubuntu more forgiving to my SATA drives?

Joe Rice

---

### Post by Joerice50 on 2009-01-29
Partial Success:

If I add PCI-nomsi to the boot string I can run Ubuntu from the CDROM

---

### Post by ya-manickill on 2009-03-18
I had a MB that used the geforce 8200 chipset on it and I had the same problems (I have upgraded my motherboard now, but it still uses the 8200 chipset...just my old one was a bit wonky)

Ok...so basically, this is a problem with the kernel and your motherboard. It, for some reason, doesnt like the SATA on the chipset. You can get around it (for just now) by adding "pci=nomsi all_generic_ide" to the bootline, which should fix it all. This, however, scales down your SATA speeds. But its a way to get around it until the fix is added into the kernel.

Almos every distro has a problem with this. Some just shove you to a busybox shell, whereas some boot and just dont see your SATA drives.

---

