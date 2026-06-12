---
title: "Wireless doesn't work anymore?"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by LaGzo on 2008-09-01
My wireless just went dead on me. It was working using ndiswrapper a few hours ago and now it doesn't work anymore. I tried following the how-to's again but no luck. What could of caused this to happen and how do I fix it? I'm running Ubuntu Hardy 64bit with broadcom 4311 rev. 2 I think.

---

### Post by prshah on 2008-09-01
> **LaGzo said:**
> My wireless just went dead on me. It was working using ndiswrapper a few hours ago and now it doesn't work anymore.

Generic solutions:

a) Try a network restart ```

sudo /etc/init.d/networking restart
```

b) Wireless switch ON?
c) Broken card?

To check (b), post the outputs of ```

lspci -v | grep -A 4 -i broadcom
sudo lshw -C network 
iwconfig
```

---

### Post by LaGzo on 2008-09-01
> **prshah said:**
> Generic solutions:

a) Try a network restart ```

sudo /etc/init.d/networking restart
```

b) Wireless switch ON?
c) Broken card?

To check (b), post the outputs of ```

lspci -v | grep -A 4 -i broadcom
sudo lshw -C network 
iwconfig
```

I get nothing when inputting the first and second codes.
iwconfig - ```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by cybrsaylr on 2008-09-01
prshah, 
I'm having the same wireless problems.
Can you help?

When I put the codes you suggest in Terminal I got this: 

 * Reconfiguring network interfaces...                                   [ OK ] 
tt@tt-laptop:~$ 
tt@tt-laptop:~$ 
tt@tt-laptop:~$ lspci -v | grep -A 4 -i broadcom
tt@tt-laptop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:9d:0d:a6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=76.180.189.242 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
tt@tt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by prshah on 2008-09-01
> **cybrsaylr said:**
> 
I'm having the same wireless problems.
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.


Unfortunately, your case is different, you're using Atheros, not broadcom. Considering this, it better you open a new thread, and for sure you can get help, and not just from me.

Atheros has to be handled differently. Some Atheros chipsets are natively supported in Ubuntu, and some need the ndiswrapper (windows drivers) route.

---

### Post by cybrsaylr on 2008-09-01
> **prshah said:**
> Unfortunately, your case is different, you're using Atheros, not broadcom. Considering this, it better you open a new thread, and for sure you can get help, and not just from me.

Thanks prshah, I will do that.

---

### Post by prshah on 2008-09-02
> **LaGzo said:**
> I get nothing when inputting the first and second codes.
iwconfig - ```
lo        no wireless extensions.
eth0      no wireless extensions.
```

Are you sure you have a broadcom; post your entire ```
lspci
```

---

### Post by LaGzo on 2008-09-09
Yes, I'm sure I have broadcom, it worked before. Its bcm4311.

```
op:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```

---

