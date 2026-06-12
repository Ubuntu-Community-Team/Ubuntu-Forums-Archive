---
title: "IC Plus IP100"
date: 2005-12-02
forum: Networking &amp; Wireless
---

### Post by Nikusan on 2005-12-02
I have an ABIT UL8 (ULI chipset, socket 939).
Everything works fine with the Breezy live CD except the onboard NIC.
Windows XP identifies it as "IC Plus IP100 10/100 Fast Ethernet".
A Google search turns up almost nothing. Can anyone help?

I searched this board and replied to a related thread but realised after I'd posted that it was in the Hoary forum so I'm posting again here. Apologies if the double post is frowned upon.

---

### Post by zwilrich on 2006-08-11
You can get a driver at [http://www.icplus.com.tw/driver-pp-IP100A.html](http://www.icplus.com.tw/driver-pp-IP100A.html)
I was able to get this driver to work with Gentoo Linux, but I haven't been able to figure out how to do it in Ubuntu yet.

---

### Post by kerneldark on 2006-08-25
I have the same nic and you have that renamed that driver folder to anything "single name" example: net. Too have that install kernel-headers, gcclib and make packages. After enter net folder and type make all. For load the driver type insmod ./sundance.ko all steps as root.
Sorry my poor english.

---

### Post by zwilrich on 2006-08-25
Thanks, I'll try it out.  I had installed make and kernel headers, but I hadn't installed gcclib.  That's probably why it didn't work.

No apologies needed for your English.  Anyone who can write an intelligent reply in a foreign language deserves congratulations.

---

