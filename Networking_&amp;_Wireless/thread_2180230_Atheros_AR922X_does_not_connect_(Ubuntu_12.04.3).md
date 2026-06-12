---
title: "Atheros AR922X does not connect (Ubuntu 12.04.3)"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by ioio10 on 2013-10-12
Hello,
I am new to Linux and I am trying to set up a new system. Problem: The PCI WLAN is not connecting i. e. network manager asks for the password (which is tripple checked and definitely right) but cannot build a connection.

Here are the informations I have found with the commands from a similar post:Code:
iwconfig
> eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




Code:
lspci -nn | grep 0280
> 04:01.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)


Code:
lspci
> 00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:16.2 IDE interface: Intel Corporation 8 Series/C220 Series Chipset Family IDE-r Controller (rev 04)
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Q87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF100GL [Quadro 4000] (rev a3)
01:00.1 Audio device: NVIDIA Corporation GF100 High Definition Audio Controller (rev a1)
03:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 41)
04:01.0 Network controller: Qualcomm Atheros AR922X Wireless Network Adapter (rev 01)

Code:
sudo lshw -C network
>   *-network               
       Beschreibung: Ethernet interface
       Produkt: Ethernet Connection I217-LM
       Hersteller: Intel Corporation
       Physische ID: 19
       Bus-Informationen: pci@0000:00:19.0
       Logischer Name: eth0
       Version: 04
       Seriennummer: 7c:05:07:0f:a7:cf
       Größe: 100Mbit/s
       Kapazität: 1Gbit/s
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=0.13-4 ip=192.168.178.35 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       Ressourcen: irq:42 memory:f6200000-f621ffff memory:f6239000-f6239fff ioport:f040(Größe=32)
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: AR922X Wireless Network Adapter
       Hersteller: Qualcomm Atheros
       Physische ID: 1
       Bus-Informationen: pci@0000:04:01.0
       Logischer Name: wlan0
       Version: 01
       Seriennummer: ac:f1:df:79:1f:19
       Breite: 32 bits
       Takt: 66MHz
       Fähigkeiten: pm bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=ath9k driverversion=3.8.0-31-generic firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       Ressourcen: irq:17 memory:f6100000-f610ffff

Code:> rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Can anyone help? Thank you in advance!

---

### Post by praseodym on 2013-10-12
Deactivate the hardware encryption of the driver:

```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by ioio10 on 2013-10-12
Thank you!!! Problem solved.

---

### Post by ioio10 on 2013-10-13
Hi,
yesterday, it worked, but today the internet couldn't connect again via WLAN...
Now I tried different things to get back to the status of yesterday, but nothing works. Probably, I did something stupid...
So here again the information:
Code:
sudo lshw -C network
 >  *-network               
       Beschreibung: Ethernet interface
       Produkt: Ethernet Connection I217-LM
       Hersteller: Intel Corporation
       Physische ID: 19
       Bus-Informationen: pci@0000:00:19.0
       Logischer Name: eth0
       Version: 04
       Seriennummer: 7c:05:07:0f:a7:cf
       Größe: 100Mbit/s
       Kapazität: 1Gbit/s
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=0.13-4 ip=192.168.178.35 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       Ressourcen: irq:42 memory:f6200000-f621ffff memory:f6239000-f6239fff ioport:f040(Größe=32)
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: AR922X Wireless Network Adapter
       Hersteller: Qualcomm Atheros
       Physische ID: 1
       Bus-Informationen: pci@0000:04:01.0
       Logischer Name: wlan0
       Version: 01
       Seriennummer: ac:f1:df:79:1f:19
       Breite: 32 bits
       Takt: 66MHz
       Fähigkeiten: pm bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=ath9k driverversion=3.8.0-31-generic firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       Ressourcen: irq:17 memory:f6100000-f610ffff


Any ideas?

Thank you!

---

### Post by praseodym on 2013-10-13
Check:
```

iwconfig
rfkill list
iwlist chan
sudo iwlist scan
ifconfig wlan0
cat /etc/resolv.conf
route -n
```

---

### Post by ioio10 on 2013-10-14
Hi,
here are the outputs. Outcome is: no effect...
Unfortunetly, I do not understand the commands. I noticed that there is TKIP in the outputs as group cipher. I use WPA+WPA2 at the fritz box, but changing to TKIP does not have an effect...

Greetings!

Code:
iwconfig
> eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
Code:
rfkill list
> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
Code:
iwlist chan
> eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
Code:
 sudo iwlist scan
> 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 24:65:11:8B:E1:52
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Madagaskar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001408f7221
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000A4D6164616761736B6172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018B0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACE131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: DD0C00040E010102010000000000
          Cell 02 - Address: 00:1A:4F:20:FE:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Joerg67"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f237d235
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 00074A6F6572673637
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 84:1B:5E:CD:70:AC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WLAN-5F6403_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003f48514ffb4
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000F574C414E2D3546363430335F455854
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B00010310470010F827EE2125E6BF0F186AB343843876331021000D4E4554474541522C20496E632E10230008574E33303030525010240008574E3330303052501042000230311054000800060050F204000110110008574E333030305250100800020084103C000101
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

Code:
ifconfig wlan0
> wlan0     Link encap:Ethernet  Hardware Adresse ac:f1:df:79:1f:19  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)

Code:
 > cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search fritz.box
ioio10@ioio10-desktop:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface



---

### Post by praseodym on 2013-10-14
Change the encryption mode to pure WPA2-AES (CCMP) and to a fixed channel. Check if a MAC-address filter is on and turn it off.

---

### Post by ioio10 on 2013-10-15
OK, seems to work for the moment.
I changed encryption and selected a fix chanel.
So I mark the thread solved and hopefully, it is!

Thank you for your help!

---

