---
title: "Connecting to wireless through wicd (BCM43xx drivers already installed)"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by SlingerXL on 2008-06-22
So I have an HP Pavilion tx 1000 with wireless card: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02). THE  My problem is that even though I can see my wireless networks (I'm trying to connect to 'girlfess'), I can't figure out how to connect to the wireless network. Wicd can't see any networks. Why is this and how do I connect?

Here's my lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:a6:9d:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.168.40 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

Here's my $sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:6A:DD:99
                    ESSID:"houseoflove"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 02:E0:62:4D:5F:38
                    ESSID:"ANY"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : none
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: 00:1B:63:2D:20:A9
                    ESSID:"girlfess"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1C:10:14:AB:84
                    ESSID:"Citgo-3"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
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
          Cell 05 - Address: 00:1E:2A:53:F6:52
                    ESSID:"511nfess"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:14:6C:F8:C2:BE
                    ESSID:"adamsinternet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by dmizer on 2008-06-23
you'll probably have to disable NetworkManager before you can use wicd.  here's how: [https://help.ubuntu.com/community/NetworkManager?#head-d279c8fbfc4d1711bb8e3a03a4b71c810878b0eb](https://help.ubuntu.com/community/NetworkManager?#head-d279c8fbfc4d1711bb8e3a03a4b71c810878b0eb)

---

### Post by Tomatz on 2008-06-23
Also you could try manually entering your SSID and password.

---

### Post by SlingerXL on 2008-06-23
> **Tomatz said:**
> Also you could try manually entering your SSID and password.

How?

---

### Post by Tomatz on 2008-06-23
> **SlingerXL said:**
> How?

Through the network manager (l-click manual setup ). The ssid is the broadcasted name of your router. You can view the ssid in your router config.

;)

---

### Post by SlingerXL on 2008-06-23
> **Tomatz said:**
> Through the network manager (l-click manual setup ). The ssid is the broadcasted name of your router. You can view the ssid in your router config.

;)
Well I know the ssid is girlfess and the password is 519. Is there a way to connect through the terminal or something? I go to System/Administration/Network but when I hit properties on wireless netowrk and enter the name and password (WPA Personal), it won't let me hit OK until I enter some IP address and gateway something or other, but I don't know what to enter there.

Also, I don't have network manager. I have wicd, so I can't manually connect through it.

---

### Post by Tomatz on 2008-06-23
> **SlingerXL said:**
> Well I know the ssid is girlfess and the password is 519. Is there a way to connect through the terminal or something? I go to System/Administration/Network but when I hit properties on wireless netowrk and enter the name and password (WPA Personal), it won't let me hit OK until I enter some IP address and gateway something or other, but I don't know what to enter there.

Also, I don't have network manager. I have wicd, so I can't manually connect through it.

Oh i see.

A quick google brought this up:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

You should be able to set up your network manually with the help of that thread as obviously you can see the network but wicd seems to be working incorrectly.

Why you using wi cd anyway the network manager should work fine with that card?

Any probs post back ;)

---

### Post by cenwesi on 2008-06-23
He seems to have the bcm43xx card... i have all sort of issue trying to get this card to connect to a WPA.  Wep works fine but ofcourse it is not that secure. 

Anyway will recommend you give the "compact-wireless" [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) a try. Using this i was able to connect to my WPA and others. Solved ALOT of the wireless problem i had. I also add to add this to my startup script in
/etc/init.d//wirelessfix.sh
#!/bin/bash
modprobe -r ssb
modprobe -r b43
sleep 5
modprobe b43
modprobe ssb

100% workes.. I even updated my Kernel this afternoon to 2.6.25 and now my hp2133 headphone sensing works.

---

