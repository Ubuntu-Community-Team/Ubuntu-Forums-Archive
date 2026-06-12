---
title: "Can't connect to the internet"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by zephyrusrain on 2008-10-08
Hey, I just installed Ubuntu Hardy Heron on my Dell Vostro 1710 and have been spending hours and hours trying to make it connect to the internet. I have done various methods to try and connect, including manually adding the DNS servers to my Network but am still unable to connect. It's dualbooted with WinXP and the internet works fine on WinXP. Any ideas how to solve my predicament? Cheers. To add I'm using a wired ADSL modem.

---

### Post by cariboo on 2008-10-08
Do you use PPPOE to connect in Wiindows? If so have a look here:

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

If you direct connect, please post the output of:

```
lspci
```

and

```
sudo lshw -C network
```

in your next post.

Jim

---

### Post by zephyrusrain on 2008-10-08
Hey Jim. I tried the PPPOE method but it still fails to work for me.

Here's what I get when I type lspci

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

And this is what I get for the other code

```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:7f:cf:ed
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-generic
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: ff
       serial: 00:21:70:9b:cc:55
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s

```

---

### Post by zephyrusrain on 2008-10-08
And also. I'm using PPPoA

---

### Post by zephyrusrain on 2008-10-08
Hey. Somehow I'm able to connect occasionally. The times where I can't connect, it detects my ethernet port as Illegal Vendor ID. But when I'm able to connect, I get the one below.

```

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:9b:cc:55
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=121.217.246.234 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

Does Hardy Heron have compatability issues with Realtek?

---

### Post by zephyrusrain on 2008-10-08
Help, anyone? My ADSL modem has a USB line as well and I've tried it. It still gives me the same problems as I had when connecting via the Ethernet cable. So it should be a problem with my Ubuntu configuration? :confused:

---

### Post by superprash2003 on 2008-10-08
please post ifconfig output.. are you able to ping your router?

---

### Post by zephyrusrain on 2008-10-08
This is what I get when I do ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:21:70:9b:cc:55  
          inet6 addr: fe80::221:70ff:fe9b:cc55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967284 overruns:0 frame:0
          TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:217 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:21:70:9b:cc:55  
          inet addr:169.254.7.172  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:217 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119064 (116.2 KB)  TX bytes:119064 (116.2 KB)


```

I'm not using a router. I'm using an ADSL modem direct.

---

### Post by Iowan on 2008-10-09
The avahi address is not usually a good sign - suggests eth0 did not successfully get an address via DHCP. Might power cycle the modem - sometimes they "lock onto" a client MAC address.

---

### Post by zephyrusrain on 2008-10-09
> **Iowan said:**
> The avahi address is not usually a good sign - suggests eth0 did not successfully get an address via DHCP. Might power cycle the modem - sometimes they "lock onto" a client MAC address.

Power cycle? What do you mean?

---

### Post by zephyrusrain on 2008-10-09
bump

---

### Post by superprash2003 on 2008-10-09
follow this [http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html](http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html) .. since its wired.. you can skip step 3 .. this would help you create a static ip..

---

### Post by zephyrusrain on 2008-10-09
Sadly that does not work as well :(

---

### Post by zephyrusrain on 2008-10-10
Bump

---

### Post by Iowan on 2008-10-10
> **zephyrusrain said:**
> Power cycle? What do you mean?Turn the power off, wait 15-20 seconds, turn power back on.

---

### Post by zephyrusrain on 2008-10-12
I thank you all for the help but I have yet to fix it. Just trying to get my laptop to connect just now took a painful 30 minutes and about 10~15 restarts.

---

### Post by zephyrusrain on 2008-10-13
bump

---

