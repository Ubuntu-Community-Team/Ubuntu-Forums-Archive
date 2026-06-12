---
title: "Wubi / Ubuntu 8.10 install fails"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Joerice50 on 2009-01-19
Hi
I am experiencing a failure to install after reboot to ubuntu following a wubi install. I am using wubi to install ubuntu 8.10 on drive e: Windows XP is installed on drive c:

If I switch on verbose reporting during ubuntu start-up the system informs me that it cannot identify either (s)ata drive 1 or (s)ata drive 2 vis 
ata failed to identify ( I/O error err_mask =0x4) eventually failing to busybox with a prompt at initramfs. 

The machine is a desktop using the XFX 8200 motherboard see [http://www.xfxforce.com/en-us/Features/8200Motherboard.aspx](http://www.xfxforce.com/en-us/Features/8200Motherboard.aspx) 

your help is appreciated as this is my first try at installing Linux and it would be nice to see it working.

Thanks in anticipation

Joe Rice

---

### Post by mgranet on 2009-01-19
Hrm. That's a tough sounding one. Does the LiveCD boot properly? Perhaps you could try reinstalling on the same partition as the Windows install. I haven't used Wubi, so I can do no more than offer basic suggestions and bump the thread.

---

### Post by Joerice50 on 2009-01-19
More information on problem:

Note the following indicates a computability problem between the mother board and SATA controller and Ubuntu rather than wubi problem:


When I run Ubuntu from a CDROM ver. 7.10 and select install I cannot install the system as disk drives are not detected.

If I look at the hardware profile a lot of items are unknown and again no disk drives are discovered

Is there anyway of forcing Ubuntu to recognise sata drives?

---

### Post by Ben Page on 2009-01-19
Why don't you try installing 8.4 or 8.10, it might be that 7.4 simply does not recognize your SATA controller. Its similar issue like when you try to install XP (no SP) on SATA HDD, it simply does not have drivers for the controller and you have to install either from floppy (drivers) or install XP SP2 or higher.
Is your MB newer production?

---

### Post by Joerice50 on 2009-01-20
Yes the mother board is new with SATA2 drive controllers, however, I am installing ubuntu 8.10 ( the newest version) and it is this version that is having problems reading the drives!

The earlier ubuntu version 7.10 which I have on a CDROM will boot in "try out" mode but will fail to detect drives if I try and install it.


So the problem is something to do with Ubuntu and the SATA2 drive controllers fitted to this motherboard.

Regards

J.Rice

---

