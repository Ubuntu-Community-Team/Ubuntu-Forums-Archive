---
title: "new  to ubunto need wirless connection"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by austin7 on 2009-05-10
:confused:umm i just installed ubuntu 8.04 on my cpu and im dual booting ith windows xp im not sure hot to get my wirless connection set up its verry frustrating i am using a dell inspiron b130 labtop if u reply could u plz tell me in verry easy steps im get confuzzed with computers easyly

---

### Post by austin7 on 2009-05-10
anyone???

---

### Post by austin7 on 2009-05-10
:confused:umm i just installed ubuntu 8.04 on my cpu and im dual booting ith windows xp im not sure hot to get my wirless connection set up its verry frustrating i am using a dell inspiron b130 labtop if u reply could u plz tell me in verry easy steps im get confuzzed with computers easyly

---

### Post by sailor2001 on 2009-05-10
click:  system/preference/network config   it's pretty straight forward

---

### Post by austin7 on 2009-05-10
i went to prefrences there is no network config

---

### Post by overdrank on 2009-05-10
> **austin7 said:**
> i went to prefrences there is no network config

Hi and welcome, you may use the command lspci in the terminal. The terminal is located under applications, accessories. Copy and paste the output here and we can try and help.

---

### Post by sailor2001 on 2009-05-10
sorry....... got to package manager (synaptics) and download: network manager

---

### Post by austin7 on 2009-05-10
do i need to be connected to internet to do this

---

### Post by austin7 on 2009-05-10
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by overdrank on 2009-05-10
> **austin7 said:**
> 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Hi and this link may help. [Broadcom 4318]("http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318+Hardy")

---

### Post by austin7 on 2009-05-10
it told me to do this
This process is vastly simplified in Hardy. The easiest way to do it is to open the Hardware Drivers program (go to the System menu in the top left corner of the screen, and click Administration, and then Hardware Drivers) and check the Broadcom B43 wireless driver box, and reboot.
Done. :KS
but when im in hardware drivers there is nothing to check

---

