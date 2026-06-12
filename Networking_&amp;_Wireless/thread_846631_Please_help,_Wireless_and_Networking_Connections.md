---
title: "Please help, Wireless and Networking Connections"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by Master_Glink on 2008-07-01
I've recently installed Ubuntu on my (somewhat)new laptop using the Wibu Installer, but I've found out I have wireless card that is not supported with the initial Ubuntu Drivers.

I've tried to set up a wired connection to download the drivers, but it didn't work either. I've also tried to install the drivers from source (I think...)as well as NDISwrapper, but I get an error while installing the everytime.

After reading the sticky, I found out that I had a "Blacklisted" RTL8187, but when I went to edit the list or to activate the driver, it wasn't there.

If anyone can help me set up my wireless internet connection I would be really grateful, I ask of you to be as detailed as you possibly can though, because I haven't had that much experience with network and wireless setting, as I've always used interfaces that allow for a scanning option and then all you have to do is to input the WEP(hex) key.

By the way the laptop I'm using is a Gateway M-1624 and I'm running the 32-bit version of Ubuntu on my 64-bit AMD Turion Processor.

Thanks in advance!

---

### Post by jualin on 2008-07-01
Post the output of > lspci from the terminal.

---

### Post by Master_Glink on 2008-07-01
> 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


There it is... I think.

---

### Post by Master_Glink on 2008-07-01
Bump!

---

### Post by Master_Glink on 2008-07-01
Bump.

---

### Post by Master_Glink on 2008-07-01
Bump.

---

### Post by jualin on 2008-07-01
Ok I just got back, let me check for a solution.

---

### Post by jualin on 2008-07-01
Ok, let's begin. Post the results of > lshw -C network

---

### Post by jualin on 2008-07-01
and since you said that your card was blacklisted you are going to need to enable the modules for the drivers. You need to run > sudo modprobe r818x
sudo modprobe r8187 Those are drivers for the RT8187 so they should work.

---

### Post by Master_Glink on 2008-07-02
Well, I tried using modprobe again, but like I said in the first post, it seems that the drivers aren't even there.

---

### Post by jualin on 2008-07-02
post the results of > lshw -C network

---

### Post by Master_Glink on 2008-07-02
Here's the output for the other command, lshw -C network:

> WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e7:e4:d5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes



---

### Post by Master_Glink on 2008-07-02
Bump.

---

### Post by jualin on 2008-07-02
From what I am seeing your wireless card is not showing up. So we wouldn't know for sure what's the model of your wireless card. Maybe someone else has another idea.

---

### Post by jualin on 2008-07-02
Have you tried moving the wireless switch?

---

### Post by Master_Glink on 2008-07-02
Well, the switch is on, I've never really moved it though.

I can also use windows to check the card if that's any help. I have windows installed in another partition using the Wibu installer.

---

### Post by Master_Glink on 2008-07-02
Bump.

---

### Post by Master_Glink on 2008-07-03
Bump!

---

### Post by Master_Glink on 2008-07-03
Bump.

---

### Post by Master_Glink on 2008-07-03
Bump.

---

### Post by Master_Glink on 2008-07-03
Bump!

---

### Post by Master_Glink on 2008-07-04
Bump.

---

### Post by jualin on 2008-07-04
Dude, I am sorry but my Ubuntu knowledge ends at this point, I don't have any more ideas of how to enable your wireless card. Maybe someone else can help you out, cause I have no idea of how to proceed after all that I have suggested. I am sorry. Make a new thread and maybe someone else more experience will help you. I will keep on looking for suggestions online and if I find something I will post it here. Sorry again!

---

### Post by rudyfella on 2008-07-08
Install ndiswrapper through Synaptic package manager and install ndisgtk for a graphical interface.

This is what I got from Brian Cantin's website. I quote from here onwards.

Easiest way is to use ndiswrapper, if you're not going to use this for security monitoring (Airocrack, etc).

Download the RTL8187B_driver_only from realtek or search google for it. Open up the INF, and look for
;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200


CHANGE IT TO

;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

insert the new inf/sys file into ndiswrapper (ndiswrapper -i /location/of/driver)

finish installing the driver with ndiswrapper, and you should be good.

---

