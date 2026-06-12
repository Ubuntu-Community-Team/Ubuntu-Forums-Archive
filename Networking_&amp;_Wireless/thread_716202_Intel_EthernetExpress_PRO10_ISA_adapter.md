---
title: "Intel EthernetExpress PRO/10 ISA adapter"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by twi124 on 2008-03-05
Intel EthernetExpress PRO/10 ISA adapter
FCC ID: EJMNIO-EPXISA1W

Anyone know where I can get the drivers to make it work, and how I'm supposed to install the drivers?  

I'm new to Ubuntu.  I just installed it about an hour an a half ago.  Any help is much appreciated.

Thanks in advance! ^_^

---

### Post by twi124 on 2008-03-06
bump

**_OS_**: *Ubuntu 7.10 Gutsy*
**_Ethernet Card_**: *Intel EtherExpress PRO/10 ISA*

I searched and found drivers for it, but none are for Ubuntu.  I'm not sure where to look next =[

Is there a way to make Ubuntu recognise my card?  
Or can someone point me in the direction of some drivers for it?

---

### Post by rowerdave on 2008-05-01
If you know the hardware type of you ISA adapter - then you are able to load the module manually.

As you have an EtherExpress Pro/10 - I'm guessing your module will be eepro

open a terminal window, try:-

**modinfo eepro**

This will list all the paramater entries needed to load the module eepro. This will *also* list any prerequisite modules which may need to be modprobed in.

List these down, and then perform a modprobe

**sudo modprobe eepro** (parameters here  eg: irq=xx)

and see if that gives you an ethx.

If there are errors, it may be due incorrect parameter entry (modprobe is strict). The command is successful if there is no text / error response.

One more things to bear in mind - configuring ISA cards means working with IRQs manually. This could result in an IRQ conflict, which the kernel cannot configure (it is not PnP). Similar to above, you will need to allocate this manually in your bios.

---

