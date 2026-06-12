---
title: "Lenovo Yoga 13, Ubuntu 12.04, Kernel 3.11, RTL8723AE Slow Wireless"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by SlvrDragon50 on 2014-03-03
1) Lenovo Yoga 13
2) ```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation 3rd Gen Core Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QS77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04)

```
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 04f3:000a Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
Bus 001 Device 007: ID 2149:2122  
Bus 001 Device 008: ID 04d9:0174 Holtek Semiconductor, Inc. 
Bus 001 Device 009: ID 0e8d:1806 MediaTek Inc. 
Bus 001 Device 010: ID 13fe:5200 Kingston Technology Company Inc. 


```

3)```
wlan0     IEEE 802.11bgn  ESSID:"Virus"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: D8:50:E6:58:46:B0   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=75/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

4)```
8723au                912139  0 

```

5)```
[    6.011152] RTL8723AU: ERROR set ssid [Virus] fw_state=0x00000008
[    6.011216] RTL8723AU: ERROR set bssid:d8:50:e6:58:46:b0
[    6.050596] RTL8723AU: ERROR start auth
[    6.055115] RTL8723AU: ERROR auth success, start assoc
[    6.058818] RTL8723AU: ERROR assoc success
[    6.058965] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.066205] RTL8723AU: ERROR send eapol packet
[    6.067965] UpdateHalRAMask8192CUsb => mac_id:0, networkType:0x0b, mask:0x000fffff
[    6.067965]      ==> rssi_level:0, rate_bitmap:0x000ff005
[    6.073729] RTL8723AU: ERROR send eapol packet
[    6.073772] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[    6.075344] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:1
[    7.267915] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[    7.316921] UpdateHalRAMask8192CUsb => mac_id:0, networkType:0x0b, mask:0x000fffff
[    7.316921]      ==> rssi_level:2, rate_bitmap:0x000ff000
[   20.360531] audit_printk_skb: 156 callbacks suppressed
[   20.360535] type=1400 audit(1393882654.623:63): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2004 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  138.641019] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/input/input15
[  138.642816] logitech-djdevice 0003:046D:C52B.000A: input,hidraw6: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:14.0-2:1
[  138.643616] input: Logitech Unifying Device. Wireless PID:400f as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/input/input16
[  138.643912] logitech-djdevice 0003:046D:C52B.000B: input,hidraw7: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:400f] on usb-0000:00:14.0-2:2
[  341.548726] RTL8723AU: ERROR send eapol packet
[  341.548966] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:2
[  341.640768] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:2
[  341.640825] RTL8723AU: ERROR send eapol packet
[  848.198336] type=1400 audit(1393883482.492:64): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=723 comm="cupsd" pid=723 comm="cupsd" capability=36  capname="block_suspend"


```

6) ```
[    6.011152] RTL8723AU: ERROR set ssid [Virus] fw_state=0x00000008
[    6.011216] RTL8723AU: ERROR set bssid:d8:50:e6:58:46:b0
[    6.050596] RTL8723AU: ERROR start auth
[    6.055115] RTL8723AU: ERROR auth success, start assoc
[    6.058818] RTL8723AU: ERROR assoc success
[    6.058965] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.066205] RTL8723AU: ERROR send eapol packet
[    6.067965] UpdateHalRAMask8192CUsb => mac_id:0, networkType:0x0b, mask:0x000fffff
[    6.067965]      ==> rssi_level:0, rate_bitmap:0x000ff005
[    6.073729] RTL8723AU: ERROR send eapol packet
[    6.073772] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[    6.075344] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:1
[    7.267915] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[    7.316921] UpdateHalRAMask8192CUsb => mac_id:0, networkType:0x0b, mask:0x000fffff
[    7.316921]      ==> rssi_level:2, rate_bitmap:0x000ff000
[   20.360531] audit_printk_skb: 156 callbacks suppressed
[   20.360535] type=1400 audit(1393882654.623:63): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2004 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  138.641019] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/input/input15
[  138.642816] logitech-djdevice 0003:046D:C52B.000A: input,hidraw6: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:14.0-2:1
[  138.643616] input: Logitech Unifying Device. Wireless PID:400f as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/input/input16
[  138.643912] logitech-djdevice 0003:046D:C52B.000B: input,hidraw7: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:400f] on usb-0000:00:14.0-2:2
[  341.548726] RTL8723AU: ERROR send eapol packet
[  341.548966] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:2
[  341.640768] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:2
[  341.640825] RTL8723AU: ERROR send eapol packet
[  848.198336] type=1400 audit(1393883482.492:64): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=723 comm="cupsd" pid=723 comm="cupsd" capability=36  capname="block_suspend"


```

7)
```
wlan0     Scan completed :
          Cell 01 - Address: D8:50:E6:58:46:B0
                    ESSID:"Virus"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDAE0050F204104A0001101044000102103B00010310470010101B62A3276E0B5198349E57D14584B2102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000852542D41433638521042001164383A35303A65363A35383A34363A62301054000800060050F20400011011000852542D4143363852100800022008103C0001031049000600372A000120
                    Quality=100/100  Signal level=72/100  
          Cell 02 - Address: D8:50:E6:58:46:B1
                    ESSID:"GuestWiFi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=71/100  


```

I am getting only 1 mbit/s on Ubuntu while I get 17 mbit/s on Windows. I've tried all these fixes with rtl_92ce_92se_92de... and keep getting module errors while I'm trying to install stuff.

---

### Post by mikailornek on 2014-03-04
check your router or modem settings and set[COLOR=#000000] "auto"[/COLOR] for [COLOR=#000000]all channel and frequency settings.[/COLOR]

---

### Post by Wernervw on 2014-10-29
Hello, i've got the same problem. Have you found a solution?

Thank you very much.

---

