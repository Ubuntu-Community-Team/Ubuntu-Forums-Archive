---
title: "Lubuntu 14.04 cannot find wireless networks or connect one manually"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by hanhylje on 2014-12-15
I installed Lubuntu 14.04 64-bit on Acer Aspire 5040.
Network manager lists no wireless networks although there are many within the reach. Also checking networks manually shows none:
```
sudo iwlist wlan0 scan
wlan0     No scan results
```


Also connecting manually does not work:
```
nmcli dev wifi connect MYNETWORK password MYPASS
Error: No network with SSID 'MYNETWORK' found.
```

Some more basics:

```
NetworkManager Tool

State: connected (global)

- Device: eth0  [LAN 1] --------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:16:D3:42:EA:E7

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.100.26
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1

    DNS:             192.168.100.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:16:CE:6F:2F:FD

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```

```
sudo lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx] [1002:5a3f]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller [1002:4372] (rev 82)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS482M [Mobility Radeon Xpress 200] [1002:5975]
06:05.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
06:06.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
```

```
rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

In case these issues are interconnected, the bluetooth management does  not work either and I get only a prompt that says that bluetooth is not  on and it should be turned on. Choosing to turn it on does not work.  This computer has hardware buttons for both bluetooth and wlan but these  do not work. (they worked in windows xp though)
Also trying to use suspend and hibernate gives GDBus error.

Any good ideas where to go from here?

---

