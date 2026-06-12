---
title: "Total Newbie, wireless help"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by suitedaces on 2009-02-23
Hi, I have a ubuntu 8.10 installed on my HP g6062ea. It is all going fine, but I have came across a stumbling block - wireless. When I right click network, and choose edit connections, it is giving me an option to edit wireless connections. Is this a sign that my wifi card is working fine, or do I still need drivers?

---

### Post by binbash on 2009-02-23
sudo iwlist scan

what is the output of this?

---

### Post by Doug11 on 2009-02-23
> **suitedaces said:**
> Hi, I have a ubuntu 8.10 installed on my HP g6062ea. It is all going fine, but I have came across a stumbling block - wireless. When I right click network, and choose edit connections, it is giving me an option to edit wireless connections. Is this a sign that my wifi card is working fine, or do I still need drivers?
Have you put your wireless settings in and tried to connect? Thats one way to find out,,if no connection,,you will probably need to find and install the right drivers for your wireless adapter.

---

### Post by suitedaces on 2009-02-23
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.



And re doug, I have put in what i think are my settings (ssid, security type and password), but cannot find bssid, mac address, etc

---

### Post by Doug11 on 2009-02-23
> **suitedaces said:**
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.



And re doug, I have put in what i think are my settings (ssid, security type and password), but cannot find bssid, mac address, etc

What is your output of this
```
lspci
```

you should see your wireless adapter listed in here.

---

### Post by suitedaces on 2009-02-23
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**


Is that it?

---

### Post by Doug11 on 2009-02-23
> **suitedaces said:**
> 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**


Is that it?

Yes, should be,,try a quick search on that and you should find a few guides on installing the correct driver. Mine is a Broadcom so the procedure is probably different

---

### Post by Doug11 on 2009-02-23
This is what you want,,
[http://ubuntuforums.org/showthread.php?t=800686&highlight=atheros+ar242x](http://ubuntuforums.org/showthread.php?t=800686&highlight=atheros+ar242x)

---

### Post by suitedaces on 2009-02-23
That is brilliant, thank you. Works like a charm.

On an aside, do you have any tips for a newbie who relies on copy & paste?

---

### Post by Doug11 on 2009-02-23
> **suitedaces said:**
> That is brilliant, thank you. Works like a charm.

On an aside, do you have any tips for a newbie who relies on copy & paste?
Not really,,i do alot of it myself,,just a matter of time getting to know the OS i guess.

---

