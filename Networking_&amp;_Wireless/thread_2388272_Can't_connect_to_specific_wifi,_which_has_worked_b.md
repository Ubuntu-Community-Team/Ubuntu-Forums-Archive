---
title: "Can't connect to specific wifi, which has worked before (Ubuntu 16.04)"
date: 2018-03-30
forum: Networking &amp; Wireless
---

### Post by mikimouse on 2018-03-30
So I have an old Dell Laptop. A Dell Inspiron 3521 it used to be connected to my wifi but one day it simply disconnected 
and I can't connect since even with the Ethernet cable. I tried connecting to other wifi networks and it works.
I had a look at a very similar thread and tried to do the same thing but it didn't help. 
The router model is DIR-895L with hardware version:A1 and software version: 1.21
[URL="http://ubuntuforums.org/showthread.php?t=2363514"]
https://ubuntuforums.org/showthread.php?t=2363514[/URL]
[https://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

So here is my pastebin:

[URL="http://paste.ubuntu.com/p/BDXBw2qWQz/"]http://paste.ubuntu.com/p/BDXBw2qWQz/
[/URL]
Please help!

---

### Post by praseodym on 2018-03-31
Please run
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by mikimouse on 2018-03-31
I just tried it and unfortunately it still doesn't connect. It sees the wifi but can't connect

---

### Post by jeremy31 on 2018-03-31
Change the encryption settings on the router so that WEP or TKIP is not used
```
          Cell 03 - Address: <MAC 'dlink-F9C0-2.4Ghz' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"dlink-F9C0-2.4Ghz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004fd15810
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by mikimouse on 2018-03-31
I think this should work. I turned off encryption on the router and the laptop connected.

The interface of the router (accessed from a different device) only gives me the option of Personal WPA/WPA2 (doesn't even specify if it is TKIP or AES)

Can you please help me out with how to use the previous code I'm not very familiar with how and where to use that code.

---

### Post by jeremy31 on 2018-04-01
The code just shows the wifi router encryption settings.  Does the router allow you to set WPA2 only without WPA

---

### Post by mikimouse on 2018-04-01
Not through the web based configuration page it only provides me with 2 options either security mode: none or security mode: WPA/WPA2 personal. 

Is there any other way to configure it other than a firmware change?

---

