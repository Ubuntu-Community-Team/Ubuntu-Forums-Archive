---
title: "Unable to switch wireless networks"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by echou127 on 2008-03-30
Hi, I am new to ubuntu.  My wireless network manager shows my network, along with others but it will not allow me to switch to my own network.  Currently, I am connected to my neighbors network which is unsecured.  My network uses a HEX key and I have entered it before and connected to my router successfully before.  My laptop always seems to connect to my neighbors router automatically when I turn it on.  When I try and switch using the appelet, my wireless does not switch.  Instead it says that i am still connected to my neighbors network, but the internet seems to disconnect after that and I can't get it to work unless i restart, and I automatically connect to my neighbors network again.  Not only can I not switch to my own network, but I also cannot switch to other unsecured networks without the same problem.

---

### Post by nixscripter on 2008-03-31
When you are connected to your neighbor's network, try pulling down the menu and select "Connect to Other Wireless Network..." See if you enter your SSID and key manually and if you will connect.

---

### Post by echou127 on 2008-04-04
I am connected to my network now but it still doesn't let me switch around.  I can't switch back to the network I was on previously.  It seems I don't have any control over what network I am connected to.  Also, if for some reason my connection fails, I don't know how to repair the connection without restarting my laptop.

---

### Post by nixscripter on 2008-04-05
When you are connected to your network, open up a terminal window, and post the output of this command: ```
sudo iwlist scan
``` (Make sure to post it in [ code ] tags so it's readable.)

---

### Post by echou127 on 2008-04-29
elsa@dell-desktop:~$ sudo iwlist scan
[sudo] password for elsa:
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:01:92:01:AC
                    ESSID:"dd-wrt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-80 dBm  Noise level=-80 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 240ms ago
          Cell 02 - Address: 00:14:BF:75:50:21
                    ESSID:"c4ndylik3wh0a"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=57/100  Signal level=-74 dBm  Noise level=-74 dBm
                    Extra: Last beacon: 8ms ago
          Cell 03 - Address: 00:11:50:94:6F:54
                    ESSID:"Belkin_Pre-N_598898"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-75 dBm  Noise level=-75 dBm
                    Extra: Last beacon: 80ms ago

eth0      Interface doesn't support scanning.

elsa@dell-desktop:~$ 


sorry it took me so long to reply.

---

### Post by TracyO on 2008-05-15
Hi Elsa,

Did you ever get your problem solved?  I'm going through the same thing now.  I just got a Dell n1525 last week with Gutsy already installed.  Last night, it was having trouble finding any network (even after restarting), and this morning, it has me on one that does not get good signal (I still cannot connect to the internet through it), and it will not allow me to switch to my normal network.  I've tried doing it manually and through simply clicking on the network connection itself.  Nothing works.  I shut down and restarted my computer, and now it is trying to connect to my usual network (it's not happening), and it still won't let me switch to go back to the bad one.  I realize that the problem may be in the network, but I'm still concerned that it's not letting me switch networks.
Here is sudo iwlist scan: (this is it still trying to connect to the usual network)

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
eth1      Scan completed : 
          Cell 01 - Address: 00:14:6C:1C:1E:06 
                    ESSID:"GETWIRED" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=42/100  Signal level=-75 dBm  Noise level=-84 dBm 
                    Extra: Last beacon: 60ms ago 
          Cell 02 - Address: 00:13:46:3F:4C:10 
                    ESSID:"default" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s 
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=45/100  Signal level=-82 dBm  Noise level=-82 dBm 
                    Extra: Last beacon: 68ms ago

---

