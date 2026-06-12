---
title: "another intel pro 3945 issue"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by hops33n on 2007-06-13
Let me know if you all need more info, but here I go.

I have a dell latitude D820 w the intel pro 3945abg card.  I installed ubuntu 7.04 twice and have the same issue.  The wireless light just keeps flashing fast.  When I finish installing an error message comes up saying:

Restricted Driver
In order for this computer to function properly, ubuntu may be using driver software that cannot be supported.
Because the software is proprietary, it cannot easily be changed to fix any future problems.
Driver: Intel(R) Pro/Wireless 3945 Network Connection driver for linux     enabled     in use

Not sure if all that tells you much or if its even needed.  From other posts, ive ran lspci and iwconfig and both have output dealing with the card.

Does the solution have to deal with the restricted repository?  If so, can I get some step by step instructions.

Thanks in advance.

---

### Post by chili555 on 2007-06-13
I don't believe there *is* a problem. Your light is flashing because it's waiting for the command to connect. Either click the Network Manager applet in the task bar and select your network and connect, or open a terminal and ```
sudo iwlist eth1 scan
```This may take a few tries. It will give you the exact ESSID of the network you want to connect to. Here's a sample:```
Cell 03 - Address: 99:13:19:62:8D:F7
                    ESSID:"myrouter1"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:42/153  Noise level:17/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
```Then do the following commands:```
sudo iwconfig eth1 essid myrouter1
sudo dhclient eth1
```Assuming no encryption, WEP, WPA or otherwie, you should connect.

Network Manager is merely a GUI interface for the above commands.

---

### Post by hops33n on 2007-06-13
Thanks for the quick response.  Just for curiosity, what is needed to connect to a wpa network.  I have some cisco aironets at work with a 64 hex password that use aes.  Thanks again.

---

### Post by chili555 on 2007-06-13
Just make sure wpa_supplicant is installed (check in Synaptic) and Network Manager should show it as an option.

---

### Post by hops33n on 2007-06-13
Now, is the network manager program the network icon under system->administration?  If so, I can see a wpa choose, just wep.  I checked and network manager and wpa_supplicant is installed.  Should I install the wpa gui?

Also, here is an output of the iwlist eth1 scan, cells 1-4 are mine, am i able to connect to any of these, I have the ssid.
wlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:18:BA:89:B1:40
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-39 dBm  Noise level=-39 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 44ms ago
          Cell 02 - Address: 00:18:BA:89:AF:D0
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-63 dBm  Noise level=-63 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 52ms ago
          Cell 03 - Address: 00:19:E8:D8:93:D0
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-89 dBm  Noise level=-89 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 724ms ago
          Cell 04 - Address: 00:40:96:32:FE:2F
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=42/100  Signal level=-84 dBm  Noise level=-84 dBm
                    Extra: Last beacon: 556ms ago

I sure appreciate the help!

---

### Post by chili555 on 2007-06-13
See the four progressively higher bars in the task bar at the top right? That's the Network Manager icon. Click it and you should be able to connect to Cell 1, which is unencrypted, with the ESSID. If you want to connect to Cell 2, you will be asked for the key and should see a drop-down to select WEP or WPA.

---

### Post by hops33n on 2007-06-13
Hey chili, hate to keep bothering with this simple mess, but I cant find the network manager icon.  I looked in synaptic and network-manager and network-manager-gnome are installed.  You mind helping me out again?

---

### Post by hops33n on 2007-06-14
Just to end this thread, I finally got it.  Thanks Chili, I turned roaming on and I could see the wifi connections.

---

