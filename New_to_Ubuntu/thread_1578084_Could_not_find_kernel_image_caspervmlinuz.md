---
title: "Could not find kernel image: /casper/vmlinuz"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by Netbook123 on 2010-09-19
I'm new to Ubuntu and I'm not really experienced in this field. I installed Ubuntu Netbook on my HP Netbook via a pendrive and the installation wen of without a hitch but now whenever I try to boot up Ubuntu through the pendrive it starts and shows the menu and at the bottom says "automatic boot will occur in 5 seconds..." or something to that effect but when the countdown reaches 0 it starts over at five. Ive tried editing some settings and reading through the help stuff but I can't find my problem. And it will say at the bottom of these other bootup menus something like boot: and if i hit enter or wait five seconds it will say below that "could not find kernel image: /casper/vmlinuz" I've tried other boot options and i'm hoping that someone here will know how to help.

---

### Post by garvinrick4 on 2010-09-19
> **Netbook123 said:**
> I'm new to Ubuntu and I'm not really experienced in this field. I installed Ubuntu Netbook on my HP Netbook via a pendrive and the installation wen of without a hitch but now whenever I try to boot up Ubuntu through the pendrive it starts and shows the menu and at the bottom says "automatic boot will occur in 5 seconds..." or something to that effect but when the countdown reaches 0 it starts over at five. Ive tried editing some settings and reading through the help stuff but I can't find my problem. And it will say at the bottom of these other bootup menus something like boot: and if i hit enter or wait five seconds it will say below that "could not find kernel image: /casper/vmlinuz" I've tried other boot options and i'm hoping that someone here will know how to help.
If you installed to hard drive it should boot without the pendrive installed. If you just want to boot off of the pendrive and it cannot find the linux kernel to boot from, just use startupdisk creator in System/Admin/startup disk creator and install a fresh install to pendrive. 
1. Download .iso file to Desktop
2. Put in flash drive
3. choose your .iso file and your pendrive in startup disk creator (make sure you choose pendrive and not hard drive)
4. Choose to format
5. slide slider over to get 4 gig of persistence.
6. install
Here is url for download.
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

---

