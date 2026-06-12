---
title: "Randomly disconnect"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by m790627 on 2008-03-17
hi all!
I've installed Ubuntu for 1 week  
but I still can't get my wireless working
I am using wicd to connect a encrypted network
with static IP
because every time I  try to use DHCP to acquire IP, it stops at "obtaining IP address"
even though the wireless is working, it's really unstable (slow, easy to disconnect) and only works while connecting to a particular router.
I've been searching for days....
but no solution was found
Please help me
Thank You!

---

### Post by jan quark on 2008-03-17
what is your wlan card?

please post the result of these terminal commands:

```
iwconfig
sudo iwlist scan
sudo lshw -C network
```

---

### Post by m790627 on 2008-03-17
ok...
here is the result
lo          no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Asus WL500W"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:60:43:A2:47   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-64 dBm  Noise level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1247   Missed beacon:0


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1D:60:43:A2:47
                    ESSID:"Asus WL500W"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=69/100  Signal level=-64 dBm  Noise level=-64 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 184ms ago


 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:1c:33:7e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=10.0.1.202 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:bd:08:68
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 link=no module=e1000 multicast=yes port=twisted pair



Thanks for dropping by!

---

### Post by m790627 on 2008-03-17
bump*

---

### Post by m790627 on 2008-03-19
bump again...*
Please help me.... I really want to use Ubuntu normally...
Thank you

---

### Post by Eiríkr on 2008-03-19
According to [this list](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel), your card has been fully supported for a while now.  Your card is the top of the list.  This makes me wonder if it might be your router that is the problem?  I had an old D-Link DI-524 that exhibited similar flakey symptoms before finally failing out entirely and refusing to work even for wired connections.  

Cheers,

Eiríkr

---

