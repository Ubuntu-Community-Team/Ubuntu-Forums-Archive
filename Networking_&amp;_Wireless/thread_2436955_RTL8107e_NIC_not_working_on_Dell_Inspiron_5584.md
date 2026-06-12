---
title: "RTL8107e NIC not working on Dell Inspiron 5584"
date: 2020-02-15
forum: Networking &amp; Wireless
---

### Post by jdak907 on 2020-02-15
Hi, any help would be greatly appreciated:
[B]
Problem:[/B] I can't get the wired network to function.

The machine is a Dell Inspiron 15-5584: [https://www.officedepot.com/a/products/8152208/Dell-Inspiron-15-5584-Laptop-156/](https://www.officedepot.com/a/products/8152208/Dell-Inspiron-15-5584-Laptop-156/)
The adapter is a Realtek rtl8107e.
This is a clean install of Ubuntu 18.04 LTS as of two days ago.
I am working on this remotely with TeamViewer and the machine is connected to WiFi.
The BIOS has the NIC enabled.
The  device I am connecting to via ethernet is a software defined radio and  is made to interface directly via ethernet, the cable and the device  have been tested and work on another Windows machine. Default IP is 192.168.10.2 - Ping test works  and lights come on.
I would like to use the WiFi for internet simultaneously with this device connected to the Ethernet port.
[B]
Observations / Troubleshooting:
[/B]
The lights on the Ethernet port don't light up when the device is plugged into it. Network GUI shows "cable unplugged".
So I did - ifdown and it says: interface enp1s0 not configured.

I have tried configuring a static IP by adding to 'interfaces', restarting network services and rebooting. I have had limited success in getting the connection to show up in the Network GUI, I can ping 192.168.10.1, but 192.168.10.2 (connected device) is not reachable.
This is what my 'interfaces' looked like after I added the interface name and static IP:
[INDENT]
```
#interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
# Interface Name #
auto enp1s0
# Static IP Address #
iface enp1s0 inet static
# IP Address #
address 192.168.10.1
# Netmask #
netmask 255.255.255.0
[/INDENT]

After I revert 'interfaces' to just:[INDENT]auto lo
iface lo inet loopback
[/INDENT]
The network adapter completely goes away in the Network GUI, all I see is VPN.



**Configuration / System Information:**

**Here is 'sudo lshw -c network':**[INDENT]radio1@radio1:~$ sudo lshw -c network
  *-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 0a
       serial: e4:54:e8:38:d9:0d
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8107e-2_0.0.2 02/26/15 ip=192.168.10.1 latency=0 link=no multicast=yes port=MII
       resources: irq:16 ioport:3000(size=256) memory:a1404000-a1404fff memory:a1400000-a1403fff
  *-network
       description: Wireless interface
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 31
       serial: ac:d5:64:7e:bf:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.3.0-28-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=192.168.0.123 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:139 memory:a1000000-a11fffff
[/INDENT]

**Here is lspci | grep Ethernet:**[INDENT]radio1@radio1:~$ lspci | grep Ethernet
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 0a)
[/INDENT]

**Here is lspci -v:**[INDENT]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 0a)
    Subsystem: Dell RTL810xE PCI Express Fast Ethernet controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at a1404000 (64-bit, non-prefetchable) [size=4K]
    Memory at a1400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable+ Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-36-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169
[/INDENT]

**Interfaces file looks like this by default:**[INDENT]
#interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
[/INDENT]
```


Thank you,
Jeff

---

### Post by wildmanne39 on 2020-02-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by jdak907 on 2020-02-16
Should text from the terminal be formatted for code tags? It's not technically code. I just indented so it would stand out. ---- edited ---- I see you added them for me, thanks. I see, it looks much better!

---

### Post by coffeecat on 2020-02-16
> **jdak907 said:**
> Should text from the terminal be formatted for code tags? It's not technically code. I just indented so it would stand out. ---- edited ---- I see you added them for me, thanks. I see, it looks much better!

As a rule of thumb, use code tags for terminal output, code, and contents of config files, or anywhere else where the simple use of spaces is used to achieve columnar formatting. If you post these in the main body of your text, the vbulletin software won't display duplicate spaces - that is, two or more spaces are shown as one, thus losing neatly aligned columns. Within code tags, the spaces are preserved.

wildemanne39 has explained how to add code tags, but there's a link in my sig for using BBCode code tags if you want something for your bookmarks.

Good luck solving your networking issue.

---

