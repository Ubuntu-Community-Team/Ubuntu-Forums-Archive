---
title: "a wireless question"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by ntlam on 2007-09-06
I just messed up my wireless and had to install it again. But it did not work yet.
When I use command: iwconfig
result:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

so it means my wireless is not detected. However when I clicked on the network manager I saw a list of wireless around my house. Can anyone explain this for me?

---

### Post by noob12 on 2007-09-06
The output of **iwconfig** will show you the current state of the device and any current association.  To see the available ones from the command line you would use:
```

sudo iwlist scan

```

---

### Post by ntlam on 2007-09-06
> **noob12 said:**
> The output of **iwconfig** will show you the current state of the device and any current association.  To see the available ones from the command line you would use:
```

sudo iwlist scan

```

Here is the result:
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:70:3E:51
                    ESSID: "linksys"
                    Protocol: IEEE 802.11g
                    Mode:Managed
                    Frequency: 2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:16:B6:B1:5D:FA
                    ESSID: "Magabs"
                    Protocol:IEEE 802.11g
                    Mode: Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1B:2F:65:E4:FC
                    ESSID:"gispi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 04 - Address: 00:15:E9:E7:88:C8
                    ESSID:"dlink"
                    Protocol: IEEE 802.11g
                    Mode: Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 05 - Address: 00:18:39:3E:66:A1
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra: bcn_int=100
                    Extra: atim=0
          Cell 06 - Address: 00:14:6C:F6:28:04
                    ESSID:"gms"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 07 - Address: 00:17:3F:0C:5C:CC
                    ESSID:"belkin54g"
                    Protocol: IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 08 - Address: 00:09:5B:73:89:04
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:90:4C:7E:00:29
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-96 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 10 - Address: 00:15:E9:DA:AC:56
                    ESSID:"wwang"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

is this good or bad news?
the wireless is not working yet

---

### Post by kevdog on 2007-09-06
OK, you should be in OK shape

Can you post the following:
lshw -C network

Of all those routers listed in the output above, which one is yours??  Are you trying to connect with either WEP or WPA?

---

### Post by ntlam on 2007-09-07
> **kevdog said:**
> OK, you should be in OK shape

Can you post the following:
lshw -C network

Of all those routers listed in the output above, which one is yours??  Are you trying to connect with either WEP or WPA?

ohh year it's working. I'm just an idiot.

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:52:f6:c1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no multicast=yes port=twisted pair
       resources: ioport:2000-20ff iomemory:88000000-88000fff irq:16
  *-network
       description: Wireless interface
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:25:60:e3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.47+,06/21/2007,5.3.0.56 ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:88200000-8820ffff irq:19

---

### Post by ntlam on 2007-09-07
I thought it remembered the network key so ...kept on reinstalling it...till i gave it the hint of my network key...

---

