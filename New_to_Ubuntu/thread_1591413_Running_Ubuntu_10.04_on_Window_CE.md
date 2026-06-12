---
title: "Running Ubuntu 10.04 on Window CE"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by Lorilorenz on 2010-10-09
I have a netbook computer with Window CE and would like to try Ubuntu 10.04 from a USB stick. I have created a bootable USB stick, but Windows CE does not recognise it. Any secrets I should know about? Any help or suggestions are greatly welcomed..

---

### Post by migs73 on 2010-10-09
When you boot, read the instructions on your BIOS page that comes up for a few seconds, and press the key it says for entering the boot set-up/order. Once there move USB to the top of the list, plug in your USB boot stick and then press whatever key the BIOS says you need to carry on. This should then boot from the USB into Ubuntu. Windows should have nothing to do with it now as everything will be run from the USB and RAM.
You will still be able to access the files on your HDD though.

---

### Post by subhkirti on 2010-10-09
Hi, 

I am trying to run my system on KUbuntu through my USB stick. I followed all the instructions, and the computer is booting from the USB. However, I am not getting my computer able to connect to the internet. Could you help me out with this? I am connecting it through a wireless LAN. 

Regards, 

Subhkirti.



> **migs73 said:**
> When you boot, read the instructions on your BIOS page that comes up for a few seconds, and press the key it says for entering the boot set-up/order. Once there move USB to the top of the list, plug in your USB boot stick and then press whatever key the BIOS says you need to carry on. This should then boot from the USB into Ubuntu. Windows should have nothing to do with it now as everything will be run from the USB and RAM.
You will still be able to access the files on your HDD though.

---

### Post by migs73 on 2010-10-09
> **subhkirti said:**
> Hi, 

I am trying to run my system on KUbuntu through my USB stick. I followed all the instructions, and the computer is booting from the USB. However, I am not getting my computer able to connect to the internet. Could you help me out with this? I am connecting it through a wireless LAN. 

Regards, 

Subhkirti.

This is a very different problem and you should start a new thread for it. Before you do though open terminal (Applications > Accessories > Terminal) and type in
```
lspci
```

Add the output of the code to the new thread, it'll tell people what type of wireless card your system has.

---

