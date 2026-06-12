---
title: "can't connect wirelessly"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Jujumasta on 2008-07-14
i have a gateway m-1617 with the marvell topdog wireless card. i followed all the instructions in [http://ubuntuforums.org/showthread.php?t=704517](http://ubuntuforums.org/showthread.php?t=704517) and now when i type ndiswrapper -l i get that the driver (netmw14x) is installed and present. however, the lo and eth0 show no wireless extensions, and i get "*NETWORK UNCLAIMED." all the options are greyed out when i try to configure the driver. any ideas on what i should do?

---

### Post by PinkFloyd102489 on 2008-07-14
Did you load the ndiswrapper module?


```
sudo modprobe ndiswrapper
```

---

### Post by adldesigner on 2008-07-14
Try the following commands:

(Lists all your PCI devices)
```
lspci
```
(Lists all your USB devices)
```
lsusb
```
(Lists your hardware and extracts Network entries)
```
sudo lshw -C -network
```
(Lists any wireless network available in your area)
```
iwlist scan
```

Post the output of each one of those commands enclosed by CODE tags (for better code readability).
This should help us start to diagnose your issue.

---

### Post by Jujumasta on 2008-07-14
lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
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
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
```

lsusb:
```
Bus 006 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 006 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:00f6 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:D1:A5:BE
                    ESSID:"Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:BF:EE:13:39
                    ESSID:"randyfrank"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=50
                    Extra:atim=0
          Cell 03 - Address: 00:18:F8:5F:91:1F
                    ESSID:"HOPPER"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1C:10:99:53:B0
                    ESSID:"chony"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

i think the sudo lshw -C -network command helped, because before when i did wlist scan it only gave me results for lo and eth0.

---

### Post by nickdbliss on 2008-07-14
> **PinkFloyd102489 said:**
> Did you load the ndiswrapper module?


```
sudo modprobe ndiswrapper
```

This command helped you actually not lshw -C network.

---

### Post by adldesigner on 2008-08-02
> **nickdbliss said:**
> This command helped you actually not lshw -C network.

Agreed.
*lshw -C Network* only lists network related hardware, buddy. :)

---

