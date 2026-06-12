---
title: "wireless issues"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by xenrix on 2010-07-31
ok i have seen the billions of threads about this but none of the explain it for the noob that i am

so heres my issue
 i installed  on a gateway t series laptop
the wireless switch is useless no matter what position its on  the :enable wireless" stays grayed out. 

so one HELP!

---

### Post by zkriesse on 2010-07-31
Could you please post the output of the following command?
```

lspci

```
If you don't know where to run this command go to [COLOR="Blue"]**Applications -> Accessories -> Terminal**[/COLOR] Type in the command and press the "[COLOR="blue"]**Enter**[/COLOR]" key. And then copy the output and paste in a reply here. Make sure to use the [COLOR="blue"]**CODE /Code**[/COLOR] tags around it!

---

### Post by gandaran on 2010-07-31
> **xenrix said:**
> ok i have seen the billions of threads about this but none of the explain it for the noob that i am

so heres my issue
 i installed  on a gateway t series laptop
the wireless switch is useless no matter what position its on  the :enable wireless" stays grayed out. 

so one HELP!
did you install the wireless drivers or check system » hardware drivers if there is one you can install, you will need cable ethernet internet to do this.
post here the results from this command so we can see what brand of wireless card you have, run in terminal
```
lspci
```

---

### Post by xenrix on 2010-07-31
ok nothing is in the driver manger or update manger

but heres what you asked for


 lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

### Post by gandaran on 2010-07-31
I don't see a wireless card, does the laptop have one?
is the wireless switch on?

---

### Post by xenrix on 2010-07-31
switch is on and the card is in

---

### Post by gandaran on 2010-07-31
is ubuntu the only system you have installed? did the wireless card work before?

---

### Post by xenrix on 2010-07-31
its the only system on this  laptop, the old hard drvie crashed so i got a new one , but yes the card worked in windows

---

### Post by xenrix on 2010-07-31
just checked its still there

---

### Post by gandaran on 2010-07-31
> **xenrix said:**
> its the only system on this  laptop, the old hard drvie crashed so i got a new one , but yes the card worked in windows
the card is not detected so maybe its broken or not properly plugged in, must be some problem with the card.

---

### Post by mantelo on 2010-08-04
Hi there,

I'm installing lucid in a T series (w350a) for a customer, and I have a similar issue. The wireless card works without issue, however it does not show in lspci (I finally found the chip on lsusb "0bda:8189 Realtek RTL8187b"). My issue is when I try to use the camera (04f2:b027 Chicony Electronics Company, Gateway USB 2.0 Webcam) wireless dies and the camera doesn't work. I have to restart to get wireless to work again.

I hope this helps somehow.

---

