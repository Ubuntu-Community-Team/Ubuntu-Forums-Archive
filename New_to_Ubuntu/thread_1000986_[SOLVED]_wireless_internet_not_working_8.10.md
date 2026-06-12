---
title: "[SOLVED] wireless internet not working 8.10"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by AnonUK on 2008-12-03
Well, today i updated 8.04 to 8.10

Before the update wireless worked fine. My laptop received the wireless signal and my neighbour's signals no problem. 

How can i make the internet work like it did before i updated ?

---

### Post by cartisdm on 2008-12-03
Hook up to a LAN and check for all the updates.  Often that fixes the problem before you need to do anything else

---

### Post by Michael.Godawski on 2008-12-03
What is your wlan card?

Please post the results of these terminal commands:
```

sudo lshw -C network
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

---

### Post by AnonUK on 2008-12-03
> **Michael.Godawski said:**
> What is your wlan card?

Please post the results of these terminal commands:
```

sudo lshw -C network
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

(i'm now posting connected to the internet via ethernet)

this was my result

```
root@anonymous-laptop:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d0:09:53
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:e7:ad:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: aa:49:05:9a:25:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@anonymous-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-57 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@anonymous-laptop:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:74:73:0D:8B
                    ESSID:"SKY03466"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-41 dBm  Noise level:-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:17:3F:EB:C8:24
                    ESSID:"Belkin_G_Plus_MIMO_785000"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-75 dBm  Noise level:-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:14:7F:5A:E1:ED
                    ESSID:"BTHomeHub-EF35"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:4/5  Signal level:-65 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 02:1D:68:00:A2:EC
                    ESSID:"BTOpenzone"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-88 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: 00:1D:68:00:A2:EB
                    ESSID:"BTHomeHub-1989"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:1E:2A:EB:53:7A
                    ESSID:"NETGEAR2"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-84 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 07 - Address: 00:16:CF:2D:A0:84
                    ESSID:"Livebox-B780"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-89 dBm  Noise level:5 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

pan0      Interface doesn't support scanning.

root@anonymous-laptop:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

Oh and before i updated. In the top right corner i could just right click to view all the wireless networks in my neighbourhood with no problem. I still can't find any wireless now :S

---

### Post by Michael.Godawski on 2008-12-03
ouch...bcm4312... broadcom often means trouble.

Check out this thread:

[http://ubuntuforums.org/showthread.php?p=5456980](http://ubuntuforums.org/showthread.php?p=5456980)

---

### Post by AnonUK on 2008-12-03
> **Michael.Godawski said:**
> ouch...bcm4312... broadcom often means trouble.

Check out this thread:

[http://ubuntuforums.org/showthread.php?p=5456980](http://ubuntuforums.org/showthread.php?p=5456980)

I deleted my linux partition. Then reinstalled 8.04

Then i let the synaptic package manager do it's updates

And voila wireless internet works.  

Although i dont see why it couldnt just work on 8.10 like on 8.04

---

### Post by cartisdm on 2008-12-03
I had to do that between the 7.10 and 8.04 upgrade.  After a few months I checked back again and they had released updates to fix my wireless problem.  Stay in touch!

---

