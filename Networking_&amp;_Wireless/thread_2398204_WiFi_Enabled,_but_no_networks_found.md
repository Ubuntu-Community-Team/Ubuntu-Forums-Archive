---
title: "WiFi Enabled, but no networks found"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by Randy M on 2018-08-08
I'm running an HP laptop (15-bso59od) dual booted between Windows 10 and Ubuntu 16.04. Wired networking works just fine, as does both wired and WiFi on Windows. When I boot to Ubuntu, WiFi shows to be enabled, but there are no networks listed. Windows shows close to a dozen. My neighbor's networks and two of mine.

I've dug through posts here and elsewhere, but none of the suggestions have helped. Here are the details for the network card.

```
iwconfig
eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

```

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eno1
       version: 15
       serial: 48:ba:4e:b2:31:92
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.205 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:4000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff
  *-network DISABLED
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 00
       serial: 40:9f:38:77:64:2d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723de driverversion=4.15.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:130 ioport:3000(size=256) memory:b1000000-b100ffff

```

and interestingly

```
iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```

Any and all help is greatly appreciated.

---

### Post by chili555 on 2018-08-08
>  *-network DISABLED
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.Disabled in this context usually means that the wireless key combination, sometimes called airplane mode, is set to disable the wireless radio. Please find it and switch it.

---

### Post by Randy M on 2018-08-08
> **chili555 said:**
> Disabled in this context usually means that the wireless key combination, sometimes called airplane mode, is set to disable the wireless radio. Please find it and switch it.

Thanks, I checked the network settings and Airplane Mode is set to off, and wireless is on. I toggled both from on to off and rebooted, but it still doesn't show any WiFi networks.

[ATTACH=CONFIG]280682[/ATTACH]

---

### Post by chili555 on 2018-08-08
I really meant the physical switch on the laptop.

What does this command tell us?```
rfkill list all
```

---

### Post by Randy M on 2018-08-08
> **chili555 said:**
> I really meant the physical switch on the laptop.

What does this command tell us?```
rfkill list all
```

There's no physical switch.

```
randy@randy-HP-Laptop-15-bs0xx:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
randy@randy-HP-Laptop-15-bs0xx:~$ 


```

---

### Post by chili555 on 2018-08-08
> **Randy M said:**
> There's no physical switch.

```
randy@randy-HP-Laptop-15-bs0xx:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
randy@randy-HP-Laptop-15-bs0xx:~$ 


```Awesome! So far, so good. Any change here?```
sudo iwlist scan
```Any clues here?```
dmesg | grep -e wlo -e rtl
```

---

### Post by Randy M on 2018-08-08
> **chili555 said:**
> Awesome! So far, so good. Any change here?```
sudo iwlist scan
```Any clues here?```
dmesg | grep -e wlo -e rtl
```

There are probably lots of clues, but only for those that know what they mean.

```
randy@randy-HP-Laptop-15-bs0xx:~$ sudo iwlist scan
[sudo] password for randy: 
lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

wlo1      Interface doesn't support scanning : Network is down

randy@randy-HP-Laptop-15-bs0xx:~$ dmesg | grep -e wlo -e rtl
[   18.416026] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   18.416028] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   18.524837] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   18.524840] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   18.656276] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   18.656279] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   18.656290] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   18.656292] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   18.982116] rtlwifi: loading out-of-tree module taints kernel.
[   18.982196] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   19.337689] rtl8723de: Using firmware rtlwifi/rtl8723defw.bin
[   19.379290] rtl8723de 0000:02:00.0: Direct firmware load for rtlwifi/rtl8723defw.bin failed with error -2
[   19.379294] rtlwifi: Selected firmware is not available
[   19.407546] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.407760] rtlwifi: rtlwifi: wireless switch is on
[   19.408917] rtl8723de 0000:02:00.0 wlo1: renamed from wlan0
[   26.551511] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
randy@randy-HP-Laptop-15-bs0xx:~$ 


```

---

### Post by chili555 on 2018-08-08
> rtl8723de 0000:02:00.0: Direct firmware load for rtlwifi/rtl8723defw.bin failed with error -2This may or may not be useful. Let's install the latest firmware.  Please follow this procedure and reboot: [https://askubuntu.com/questions/1061846/installing-driver/1061891#1061891](https://askubuntu.com/questions/1061846/installing-driver/1061891#1061891)

Now can you scan?

This may also be helpful: [https://askubuntu.com/questions/1037323/wifi-speed-on-my-laptop-is-a-bit-slow-and-its-range-is-also-very-low-what-to-do/1037813#1037813](https://askubuntu.com/questions/1037323/wifi-speed-on-my-laptop-is-a-bit-slow-and-its-range-is-also-very-low-what-to-do/1037813#1037813)

I will have to pick this up again in about 10 hours.

---

### Post by Randy M on 2018-08-08
> **chili555 said:**
> This may or may not be useful. Let's install the latest firmware.  Please follow this procedure and reboot: [https://askubuntu.com/questions/1061846/installing-driver/1061891#1061891](https://askubuntu.com/questions/1061846/installing-driver/1061891#1061891)

Now can you scan?

This may also be helpful: [https://askubuntu.com/questions/1037323/wifi-speed-on-my-laptop-is-a-bit-slow-and-its-range-is-also-very-low-what-to-do/1037813#1037813](https://askubuntu.com/questions/1037323/wifi-speed-on-my-laptop-is-a-bit-slow-and-its-range-is-also-very-low-what-to-do/1037813#1037813)

I will have to pick this up again in about 10 hours.

Progress! I can scan now, and it shows two connections. Both are mine, but neither will connect. I tried the link that shows how to improve range, but I couldn't get it to find the adapter. I don't think that's the issue, though. The router is about 10 feet from the laptop.

I, too, will have to sideline this until tomorrow after work. Thanks again for getting me this far.

```
randy@randy-HP-Laptop-15-bs0xx:~$ sudo iwlist scan
wlo1      Scan completed :
          Cell 01 - Address: C0:C1:C0:CF:8C:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Guairdean 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c609ae80d
                    Extra: Last beacon: 740ms ago
                    IE: Unknown: 000D47756169726465616E20322E34
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700105D225F13A6DCE9A7F4F6AF42EA5A989D10210005436973636F1023000D4C696E6B7379732045343230301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180200F0240000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 48:5D:36:48:97:D6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"evilsnowbeanie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016026dc518b
                    Extra: Last beacon: 17328ms ago
                    IE: Unknown: 000E6576696C736E6F776265616E6965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD310050F204104A000110104400010210470010325EA7429BF620DF6B30872C7CBE0892103C0001031049000600372A000120
                    IE: Unknown: DD090010180206001C0000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

randy@randy-HP-Laptop-15-bs0xx:~$ 


```

---

### Post by chili555 on 2018-08-09
> I don't think that's the issue, though. The router is about 10 feet from the laptop.
I think it's *exactly* the issue:> Cell 01 - Address: C0:C1:C0:CF:8C:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                   [COLOR="#FF0000"] Quality=33/70 [/COLOR] Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Guairdean 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:MasterPlease open a terminal and do:```
sudo -i
echo "options rtl8723de ant_sel=2"  >  /etc/modprobe.d/rtl8723de.conf
exit
```Reboot and scan:```
sudo iwlist scan
```Is there any improvement? If not, then:```
sudo -i
echo "options rtl8723de ant_sel=1"  >  /etc/modprobe.d/rtl8723de.conf
exit
```Reboot and scan again. One of the two, I believe, will be a huge improvement.

For what it's worth, my scan from 10 feet from the router is:```

Cell 04 - Address: xx:2B:B0:DC:45:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    [COLOR="#FF0000"]Quality=70/70 [/COLOR] Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
<snip>
```

---

### Post by Randy M on 2018-08-09
> **chili555 said:**
> I think it's *exactly* the issue:Please open a terminal and do:```
sudo -i
echo "options rtl8723de ant_sel=2"  >  /etc/modprobe.d/rtl8723de.conf
exit
```Reboot and scan:```
sudo iwlist scan
```Is there any improvement? If not, then:```
sudo -i
echo "options rtl8723de ant_sel=1"  >  /etc/modprobe.d/rtl8723de.conf
exit
```Reboot and scan again. One of the two, I believe, will be a huge improvement.

For what it's worth, my scan from 10 feet from the router is:```

Cell 04 - Address: xx:2B:B0:DC:45:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    [COLOR=#FF0000]Quality=70/70 [/COLOR] Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
<snip>
```

 
Success! Many thanks for your patience.

```
randy@randy-HP-Laptop-15-bs0xx:~$ sudo iwlist scan
[sudo] password for randy: 
wlo1      Scan completed :
          Cell 01 - Address: 48:5D:36:80:CA:F2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"FiOS-RJR3E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001694ddd8748
                    Extra: Last beacon: 1028ms ago
                    IE: Unknown: 000A46694F532D524A523345
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD780050F204104A0001101044000102103B000103104700108E5735706E5AC0F1CB9B6EDF71C2A9C010210009477265656E5761766510230003424852102400013410420001311054000800060050F20400011011000E477265656E576176652042485234100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 02 - Address: B0:7F:B9:01:B9:D3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011e33c80f9
                    Extra: Last beacon: 1104ms ago
                    IE: Unknown: 00094E4554474541523730
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050200200000
                    IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD830050F204104A0001101044000102103B000103104700103600D1F2C84062311BD69B790C6442B5102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000C43333030302D3130304E4153100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 03 - Address: 38:35:FB:99:4B:D6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MySpectrumWiFid0-5G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000134065e73a2
                    Extra: Last beacon: 844ms ago
                    IE: Unknown: 00134D79537065637472756D5769466964302D3547
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 7F0800000F0000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: A0:63:91:2C:3E:6F
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026ac5211d08
                    Extra: Last beacon: 520ms ago
                    IE: Unknown: 00094E4554474541523133
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050500170000
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1608080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD7A0050F204104A0001101044000102103B000103104700103F2B15E26D18AB7EEECEDDAD33D695041021000D4E4554474541522C20496E632E1023000552373030301024000552373030301042000233321054000800060050F2040001101100055237303030100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180205001C0000
                    IE: Unknown: DD180050F2020101880003A4000027A400004243BC0062326600
                    IE: Unknown: 46057200010000
                    IE: Unknown: DD1E00904C0408BF0CB259820FEAFF0000EAFF0000C0050008000000C3020002
          Cell 05 - Address: 48:5D:36:48:97:D6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"evilsnowbeanie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001694d822a48
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 000E6576696C736E6F776265616E6965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD780050F204104A0001101044000102103B00010310470010325EA7429BF620DF6B30872C7CBE089210210009477265656E5761766510230003424852102400013410420001311054000800060050F20400011011000E477265656E576176652042485234100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180205001C0000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 06 - Address: F4:30:B9:DF:9E:C6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-C5-HP OfficeJet 3830"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002586bac4d8
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 001B4449524543542D43352D4850204F66666963654A65742033383330
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: Unknown: 23021300
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A20001AFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200000C0000
                    IE: Unknown: DD180050F202010188000364000027A4000041435E0061322F00
                    IE: Unknown: DDC40050F204104A000110104400010210570001011041000100103B000103104700101C852A4DB8001F08ABCDF430B9DF9EC5102100024850102300164F66666963654A65742033383330207365726965730010240005333833300010420010434E373743335133524B3036363400001054000800030050F20400051011001B4449524543542D43352D4850204F66666963654A657420333833301008000200001049000600372A00012010490017000137100600101C852A4DB8001F08ABCDF430B9DF9EC5
                    IE: Unknown: DD640800090004000000070102010003164F66666963654A657420333833302073657269657300040533383330000510434E373743335133524B30363634000006101C852A4DB8001F08ABCDF430B9DF9EC50704C0A801C2080200C4090200080A0400000001
          Cell 07 - Address: 48:5D:36:A0:85:FA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"FiOS-01DKJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001601573e8a
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 000A46694F532D3031444B4A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD780050F204104A0001101044000102103B0001031047001047429A11DD831389FA70A49FB865681510210009477265656E5761766510230003424852102400013410420001311054000800060050F20400011011000E477265656E576176652042485234100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180204001C0000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 08 - Address: 0C:EA:C9:4B:A7:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Frontier9120"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002120d49285
                    Extra: Last beacon: 14144ms ago
                    IE: Unknown: 000C46726F6E7469657239313230
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23020E00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050200370000
                    IE: Unknown: 46053208010000
                    IE: Unknown: 2D1AAD091FFFFFFF0000000000000080017800000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD090010180202101C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 09 - Address: C0:C1:C0:CF:8C:01
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Guairdean 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002586384c02
                    Extra: Last beacon: 1036ms ago
                    IE: Unknown: 000D47756169726465616E20322E34
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700105D225F13A6DCE9A7F4F6AF42EA5A989D10210005436973636F1023000D4C696E6B7379732045343230301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180200F0240000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: 50:C7:BF:47:A7:5E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_A75F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003714d173
                    Extra: Last beacon: 420ms ago
                    IE: Unknown: 000C54502D4C494E4B5F41373546
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B0503003C0000
                    IE: Unknown: 2D1AAD0117FFFFFFFF00000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD940050F204104A0001101044000102103B00010310470010D96C7EFC2F8938F1EFBD6E5148BFA8121021000754502D4C494E4B1023000C41726368657220433534303010240006313233343536104200033030311054000800060050F20400011011001C576972656C65737320526F7574657220417263686572204335343030100800022008103C0001031049000600372A000120
                    IE: Unknown: DD1E00904C0418BF0CB279830FAAFF0000AAFF0000C005000B000000C3020002
                    IE: Unknown: DD090010180203001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 11 - Address: CA:3A:6B:2F:3B:EC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001694d81804a
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0721555320010B802401802801802C01803001809501809901809D0180A10180A50180
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C081FFFFF00000000000000002C010100000000000000000000
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435D0062322E00
                    IE: Unknown: DD3C0050F204104A00011010440001021049000600372A00012010110014526F6B752053747265616D696E6720537469636B1054000800070050F2040001
                    IE: Unknown: DD12506F9A09020200210B030600CA3A6B2F3BEC
                    IE: Unknown: DD0D506F9A0A00000601111C440032

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

randy@randy-HP-Laptop-15-bs0xx:~$ 


```

---

### Post by chili555 on 2018-08-09
> Cell 09 - Address: C0:C1:C0:CF:8C:01
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    [COLOR="#FF0000"]Quality=67/70 [/COLOR] Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Guairdean 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:MasterVery nice!

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

Glad it's working.

---

