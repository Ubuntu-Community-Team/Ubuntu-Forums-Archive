---
title: "Network problems - network unclaimed"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by hr_giger on 2011-02-04
Hi, 

I have just done an install of 10.04 on a new laptop

I was expecting Network Manager to be able to pick up my network devices, but it found nothing, wired or wireless. 

I had a look around the forums, and suspect that ubuntu doesn't support my network card, but I'm not sure. I have included some of the output people requested from similar problems below. If you need anything please ask.

As far as I can tell, there is no 'eth0', or eth(anythingelse), if that means anything...

Thanks


amanda@amanda-laptop:~$ sudo lshw -C  network
[sudo] password for amanda: 
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:ff600000-ff603fff

amanda@amanda-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: Toshiba America Info Systems Device [1179:9602]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64,  Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)

---

### Post by DiSTORT3D on 2011-02-04
```
sudo nano /etc/network/interfaces
```

add: 

```
auto eth0
iface eth0 inet dhcp
```

```
/etc/init.d/networking restart
```

---

### Post by hr_giger on 2011-02-05
Well, that sorta worked. 

I can now get onto the internet via a cable connection. Except the wired connection wasn't recognised by Network Manager. I let Ubuntu do all its updates and stuff, and then restarted, and Network Manager has disappeared completely. 

The notification area is still locked to the panel, and when I try 

amanda-laptop:~$
nw-applet 

in a terminal 

I get

amanda-laptop:~$
An instance of nm-applet is already running.

** (nm-applet:1735): warning **: <WARN> constructor(): Couldn't initialize the D-Bus manager. 

I've tried killing it and restarting, but I get the same thing. 


I'm also trying to set up my wireless. But obviously Network Manager can't see it. 

There's no wlan0 listed under iwconfig.

I tried adding it in a similar way to you suggested above, but it is not recognised. 

Any ideas?


Thanks.

---

### Post by hr_giger on 2011-02-05
Well, the network manager icon is back. Not sure why. 

But it doesn't recognise my wired connection, or list any wireless networks. 

Any ideas what's going on?

---

### Post by hr_giger on 2011-02-05
iwconfig info:

amanda@amanda-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

amanda@amanda-laptop:~$

---

### Post by kevdog on 2011-02-05
The unclaimed refers to the driver or kernel module -- there is no current driver or kernel module contained within your base install that "claims" the device -- meaning you will have to find a driver and install it for your card to work.

---

### Post by walt.smith1960 on 2011-02-05
The vendor I.D. indicates an RealTek RTL8188CE chipset.  If you search for that in the wireless & networking forum, you might find useful info.  HTH,

---

### Post by JKyleOKC on 2011-02-05
Just today I came across something in my /usr/share/doc/network-manager directory that may help: ```
The config to select unmanaged/managed mode is 
in /etc/NetworkManager/nm-system-settings.conf:

  [ifupdown]
  managed=true/false

Unmanaged mode will make NetworkManager not touch any wired/wireless device matching
an interface name configured in /etc/network/interfaces.

Managed mode will make NetworkManager manage all devices and will make NetworkManager
honour all dhcp and static configurations for wired and wireless devices.

The default mode shipped in Ubuntu/intrepid is "unmanaged".

```You would have to use "sudo gedit /etc/NetworkManager/nm-system-settings.conf" to make the change/addition, and I've not tested this to see if it still works on versions more recent than Intrepid Ibis, but it might well make a difference...

---

### Post by hr_giger on 2011-02-17
Hey, 

I did as you (walt.smith) suggested and came across this thread:

[http://ubuntuforums.org/showthread.php?t=1604101&highlight=RealTek+RTL8188CE](http://ubuntuforums.org/showthread.php?t=1604101&highlight=RealTek+RTL8188CE)

and after following the instructions in post 6 (dushyanthan) everything works. 

Thanks so much.

Mark

---

### Post by walt.smith1960 on 2011-02-17
:d :d

---

