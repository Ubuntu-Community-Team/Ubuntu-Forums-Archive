---
title: "USB wireless adapter wnda3100v2"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by kent14 on 2015-01-11
New to ubuntu, i really just dont want to pay for windows.  It also seems really cool how much free software there is for linux. Anyways...

I breifly had Ubuntu before, but i had it hooked up via ethernet.  At the house im living at now its not practical long term, but its what im using now.  I went to walmart today and bought an adapter.  The netgear N600 Dual Band USB adapter looked like a good buy, but i fear i was so so so wrong.

I have been looking at forums here and forums there, typing commands into the terminal, what Im getting at is that i cant track all the steps i have taken thus far. So this isnt going to be the most detailed explaination ever, but please just tell me what to do and ill respopnd back with the corresponding information.

Found some drivers on this one random thread and downloaded them.  In Ndiswrapper, both the 64bit and 32bit installed. I thought i had a fix for this whole ordeal.

Underneath "bcmn43xx32", in ndiswrapper, it says "Harware present: Yes"

I'm assuming, now please correct me if im wrong, as i probly am, that this means that i have installed a driver for the adapter and Ndiswrapper detects it.  The problem is that when i look for open wireless connections there is nothing.

I have a feeling that i need to start over from square one but i do not know where that is.  I am using the new ubuntu.  I'm pretty sure v14.04 is the version number.

I'm kinda sleepy as its 4:46 in the morning and I am having a hard time proof reading this.  Please help me if you have an idea on how to fix this issue im having.

---

### Post by praseodym on 2015-01-11
Hi,
please run the wireless script from the sticky thread and show the outputs, plus
```

ndiswrapper -l
dmesg | grep ndis
```

---

### Post by kent14 on 2015-01-11
kent@kent-MS-7693:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present
kent@kent-MS-7693:~$ dmesg |grep ndis
[   10.053531] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   10.054528] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   12.648059] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   12.648093] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[   12.648415] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[   12.648494] usbcore: registered new interface driver ndiswrapper
kent@kent-MS-7693:~$

---

### Post by kent14 on 2015-01-11
i should also mention that i had deleted the 64bit driver as it was installed correctly but did not state that it recongnized the hardware as the 32bit driver did.  so i deleted it.  

If Im coming across as an idiot who is wasteing your time please just give me a list of things i need to understand, a link with instructions that seems to work, or i can start over and do a step by step thread on what im doing.

I suppose i could buy one of these panda usb routers that i heard a dude talking about.  Anyone know if they are a solid buy for a linux pc? or what usb wifi adapter is a solid buy for linux?

But please if you still think you may be able to help then just tell me what to do.

Thanks
Kent

---

### Post by praseodym on 2015-01-11
```
 [ 12.648059] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
```
Try this 64bit driver:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

---

### Post by kent14 on 2015-01-11
> **praseodym said:**
> ```
 [ 12.648059] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
```
Try this 64bit driver:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

I added this driver and it works.  Thanks a lot man, like seriously, thank you.

---

### Post by praseodym on 2015-01-12
Glad it worked. Please mark the thread [SOLVED] using Thread tools

---

### Post by hector13 on 2015-01-17
Hi guys
I'm new in Ubuntu and I'm trying to install the driver to my NetGear WNDA3100v2 802.11abgn [Broadcom BCM4323]. ID 0846:9011.
I'm not sure the driver indicated above will work, and how to install it.
Could anyone give me a hand with this? ;-)
H

---

### Post by praseodym on 2015-01-17
Hi,

can you hook-up temporarily via cable? If yes, please run
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
```
After that install the driver via the "Windows WLAN" tool

---

