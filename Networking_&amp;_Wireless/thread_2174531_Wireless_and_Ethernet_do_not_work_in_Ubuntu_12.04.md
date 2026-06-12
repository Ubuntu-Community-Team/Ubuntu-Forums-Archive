---
title: "Wireless and Ethernet do not work in Ubuntu 12.04"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by bobschleisky on 2013-09-15
I installed Ubuntu 12.04 on my computer using Wubi recently, and I'm unable to connect to the internet using either Ethernet or Wireless. At first, it was showing these errors while starting up:

```

    ERROR: Firmware file "b43/ucode.fu" not found
    ERROR: Firmware file "b43-open/ucode15.fu" not found
    ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver

```

I was able to install the b43 driver and now it no longer shows those errors starting up and displays "enable wireless" when I click on the network icon, but neither ethernet or wireless work still.

I looked through some previous threads about this, but was unable to fix this problem using those solutions. Please help!


result of `ifconfig`:

```

    eth0      Link encap:Ethernet  HWaddr 00:23:8b:d3:0e:8d  
              inet6 addr: fe80::223:8bff:fed3:e8d/64 Scope:Link
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:168 (168.0 B)

    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:200 errors:0 dropped:0 overruns:0 frame:0
              TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:16072 (16.0 KB)  TX bytes:16072 (16.0 KB)

    wlan0     Link encap:Ethernet  HWaddr 00:25:56:40:72:d9  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

result of `lspci`:

```

    00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
    00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
    00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
    02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

result of: `cat /etc/network/interfaces`:

```

    auto lo
    iface lo inet loopback

```

---

### Post by varunendra on 2013-09-15
Welcome to the forums bobschleisky ! :)

Your wireless should be easier part. Please download linux-firmware-nonfree package from [here]("http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download"), copy to your Ubuntu machine, and double-click to install. Then reboot or simply do-
```
sudo modprobe -rv b43
sudo modprobe -v b43
```

Once your wireless is up, we can focus on ethernet part.

Please post the output of -
```
lspci -nnk | grep -iA2 net
```

**PS:**
For posting output codes, please use 'Code' box. To see how to use it, please follow the "Using Code Tags" link in my signature.

---

### Post by Bucky Ball on 2013-09-15
*Thread moved to **Networking & Wireless**.*

Welcome. Be aware: Wubi is not really considered a permanent solution, more for trying Ubuntu to see if you like it before a full install to hard drive. There aren't a lot of Wubi gurus here as a result. You are in good hands with the wifi issue, nonetheless.

---

### Post by bobschleisky on 2013-09-15
Hey, Thanks for helping me out with this problem!

I reinstalled ubuntu using Wubi and then installed the [COLOR=#000000] linux-firmware-nonfree package that you linked to.

Afterwards, there are options for wireless connections under the network icon, but it does not list available wireless networks to connect to. 


This is what I get after running [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net:

[/FONT][/COLOR]```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: b43-pci-bridge
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3627]
    Kernel driver in use: r8169

```

---

### Post by varunendra on 2013-09-15
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

**PS:**
If you are considering any serious usage of Ubuntu, you should do a full install instead of using WUBI, like BB said above. WUBI breaks often and is meant for only testing Ubuntu on windows computers.

---

