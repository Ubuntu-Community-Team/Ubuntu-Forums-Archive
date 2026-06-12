---
title: "I cant get 1024x768 screen resolution in UBUNTU 9.10"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by damodar.narayanan on 2010-05-07
I am not able to get 1024x768 screen resolution in UBUNTU 9.10. 

The output of lspci command is given below:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Could someone help me fix this problem and make my screen resolution to 1024x768.

Thanks

---

### Post by narendraD on 2010-05-07
First, you need Hardware drivers for your Video. If you already have them then changing res is simple. the driver will appear in System menu. 

The other option is to edit your Xorg.conf file in /etc/X11 
Backup the Xorg.conf file somewhere first. Then
using command sudo gedit /etc/X11/Oorg.conf and add the resolution to the Monitor section as below. Note: The whole code is just given for clarity You only need to add the Mode line as given

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768"
    EndSubSection
EndSection

---

### Post by Mark Phelps on 2010-05-07
Ignore the comment about hardware drivers -- that applies to ATI & Nividia chipsets, not to Intel chipsets.

Intel drivers are installed by default.

---

