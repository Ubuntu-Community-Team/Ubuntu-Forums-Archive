---
title: "Feisty Network Troubles - Belkin F5D7011 + bcwml5"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by giambrone on 2007-05-14
Okay guys - just wiped Windows off the old laptop to regain some of its usability, and I've encountered wireless troubles. I've followed various howto's etc and still there is no joy. Sometimes the card comes on, sometimes it doesn't, sometimes the card is recognised, sometimes it isnt - I'm guessing driver issues. Anyway, onto the real trouble - when it does work, I can see the network and connect (the green dots don't appear...hrmm) but I still don't have an internet connection!

Anyway I appear to be taking a rather long-winded approach to this, and so any help will be appreciated.

Matt :KS

---

### Post by giambrone on 2007-05-17
**bump**

UPDATE - Still no joy!!

---

### Post by epee on 2007-05-17
You'll need to post some details:

What do you get for *iwconfig* or *iwlist scan*?

What's in /etc/network/interfaces?

What have you tried already?

---

### Post by giambrone on 2007-05-21
Okay Here We Go...

++UPDATE++ I have to modprobe ndiswrapper everytime I want the card to turn on... Still no further progress wireless-wise.

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:39:6F:9D
                    ESSID:"paulton"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
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
          Cell 02 - Address: 00:18:4D:00:3D:A4
                    ESSID:"EASYSTOP"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
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
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK

##Paulton is the network I want##

/etc/network/interfaces:
> 

auto lo
iface lo inet loopback


iface eth0 inet dhcp



[I followed this HOWTO:]("http://ubuntuforums.org/showthread.php?t=201902")

Thanks in advance...

Matt:KS

---

### Post by Kobalt on 2007-05-21
If you have to modprobe ndiswrapper to get your card on then it might not be loaded at boot. Check your /etc/modules file to see if ndiswrapper is listed in there. If it's not add it : ```
gksu gedit /etc/modules
```

---

### Post by giambrone on 2007-05-21
Just to check - I add "ndiswrapper" (without quotations) at the bottom of the list???

Thanks,
Matt:KS

---

### Post by theironchef on 2007-05-26
[http://ubuntuforums.org/showthread.php?t=455569](http://ubuntuforums.org/showthread.php?t=455569)

---

