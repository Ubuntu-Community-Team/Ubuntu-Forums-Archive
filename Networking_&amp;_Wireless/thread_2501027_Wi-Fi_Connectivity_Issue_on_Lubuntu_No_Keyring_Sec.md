---
title: "Wi-Fi Connectivity Issue on Lubuntu: No Keyring Secrets Found"
date: 2024-09-19
forum: Networking &amp; Wireless
---

### Post by aymanhammadi on 2024-09-19
Hello,
I’m experiencing an issue with Wi-Fi connectivity on my Lubuntu system. When attempting to connect to a Wi-Fi network that requires a password, I receive the following message:
```
nm-applet-Message: No keyring secrets found for <network-name>/802-11-wireless-security; asking user.
```


Here are some additional details about my system and the issue:

**System Information:**

[LIST]
[*]**Distribution:** Lubuntu 24.04.1 LTS 
[*]**Kernel Version:** 6.8.0-45-generic 
[/LIST]
**Network Hardware:**

[LIST]
[*]**Ethernet Controller:** Intel Ethernet Connection I218-LM 
[*]**Wireless Adapter:** Realtek RTL8192EE PCIe Wireless Network Adapter 
[/LIST]

**Commands and Outputs:**
**lspci -nnk | grep -iA3 net:**

```

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
        Subsystem: Lenovo ThinkPad X240 [17aa:2214]
        Kernel driver in use: e1000e
        Kernel modules: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:001b]
        Kernel driver in use: rtl8192ee
        Kernel modules: rtl8192ee, wl


```

**iwconfig:**
```
lo        no wireless extensions.

enp0s25   no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```

[B]sudo lshw -C network:
[/B]```
*-network                 
     description: Wireless interface
     product: RTL8192EE PCIe Wireless Network Adapter
     vendor: Realtek Semiconductor Co., Ltd.
     logical name: wlp3s0
     driver=rtl8192ee
     firmware=N/A

```

**What I’ve Tried:**

[LIST]
[*]Reinstalled Network Manager and network-manager-gnome. 
[*]Verified the network adapter is recognized and drivers are installed.  
[/LIST]

**Issue:** When trying to connect to a Wi-Fi network with a password, Network Manager prompts for keyring secrets but does not store or use them properly, resulting in connection failures.

---

