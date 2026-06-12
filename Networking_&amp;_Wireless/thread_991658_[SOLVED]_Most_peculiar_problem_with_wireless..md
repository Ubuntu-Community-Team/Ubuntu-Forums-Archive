---
title: "[SOLVED] Most peculiar problem with wireless."
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by MaDaucer on 2008-11-24
Im running Kubuntu 8.10 with a relatively fresh install (installed 23 Nov 2008 ) on an Acer  Aspire 3694WLMI.

After install the wifi did not work, but i managed to install drivers (atleast i think so, I'm kinda new to linux) and get it working more or less according to the instructions from this url:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction)

The problem now is that i can see 4 wireless networks, but not my own.
I know my wlan is up and running because i can connect to it from my xbox 360 and my wife can connect from her Vista-laptop.

Even rebooting the wireless router does not bring it to the wifi-list of this kubuntu-laptop.

I dont have means of testing a connection since they are protected, and I dont know the owners.

Help would be greatly appreciated.

---

### Post by sambarusty on 2008-11-24
So you can see your neighbours networks, but not the one in your house?  You are not even seeing it show up as encrypted or something silly of that nature?  I would think if you are seeing networks at all, then your hardware is set-up properly.

---

### Post by sambarusty on 2008-11-24
Which standard is your router?  802.11 what?

---

### Post by MaDaucer on 2008-11-24
Yes, I can see my neighbours networks, but not my own. And, like I said.. my network is up and running (2 devices connected to it) but for some reason my Kubuntu laptop cannot see it.

I haven't a clue what to do or where to start searching the problem.

---

### Post by Bucky Ball on 2008-11-24
System->Administration->Network. Check your configuration is set to "Automatic Configuration (DHCP)", 'Enable Roaming' is switched off, you have the correct ESSID and security details etc.

ps: just remembered you are in KDE, so there should be something equivalent in there. Don't use it myself so sorry can't be more specific.

---

### Post by MaDaucer on 2008-11-24
> **sambarusty said:**
> Which standard is your router?  802.11 what?

802.11g / 2.4GHz D-link

---

### Post by MaDaucer on 2008-11-24
> **Bucky Ball said:**
> System->Administration->Network. Check your configuration is set to "Automatic Configuration (DHCP)", 'Enable Roaming' is switched off, you have the correct ESSID and security details etc.

ps: just remembered you are in KDE, so there should be something equivalent in there. Don't use it myself so sorry can't be more specific.


I've checked all this and they were as they were supposed to be. I am certain that the ESSID and the rest of the security details are correct (checked with the second laptop).

---

### Post by MaDaucer on 2008-11-24
any one have an idea about this?

I've checked around the web for a possible solution with no success.

---

### Post by Bucky Ball on 2008-11-24
Could you post the result of 

```
iwconfig
```

... please?

---

### Post by MaDaucer on 2008-11-24
> **Bucky Ball said:**
> Could you post the result of 

```
iwconfig
```

... please?

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

this is the result of 'iwconfig'. Sorry I didnt reply earlier (I was taking a nap).

---

### Post by Bucky Ball on 2008-11-24
```
Access Point: Not-Associated
```

Okay, this is obviously your problem, everything else looks fine so looks like you successfully installed the driver. One question: which driver?

Could you now post the result of:

```
sudo iwlist wlan0 scan
```

---

### Post by MaDaucer on 2008-11-24
```
sudo iwlist wlan0 scan
``` returns the following:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:13:49:43:3E:A4
                    ESSID:"Susku"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/100  Signal level:-76 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001d323e4121
                    Extra: Last beacon: 304ms ago
          Cell 02 - Address: 00:14:BF:48:6C:42
                    ESSID:"jlan2"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level:-70 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000c5d2bfc18e
                    Extra: Last beacon: 92ms ago
```

Oh and my wlan-networks ESSID is plain 'madaucer' which does not appear in the scan.

---

### Post by MaDaucer on 2008-11-26
```

wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:D8:85:FE
                    ESSID:"madaucer"          
                    Mode:Master               
                    Channel:6                 
                    Frequency:2.437 GHz (Channel 6)
                    Quality=75/100  Signal level:-50 dBm  Noise level=-72 dBm
                    Encryption key:on                                        
                    IE: IEEE 802.11i/WPA2 Version 1                          
                        Group Cipher : TKIP                                  
                        Pairwise Ciphers (2) : TKIP CCMP                     
                        Authentication Suites (1) : PSK                      
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s      
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s     
                              48 Mb/s; 54 Mb/s                               
                    Extra:tsf=0000000f14f3219b                               
                    Extra: Last beacon: 20ms ago

```

Problem solved.
I'm not sure what exactly I did to get it working, but 1st I reset my wlan-box, set the same settings on it and lowered the channel number (previously 13).

Then I reinstalled the drivers using the same guide as before, rebooted and voila, the wireless network magically appeared to the scan list.

---

### Post by Bucky Ball on 2008-11-26
Excellent news! Mark as 'solved' from Thread Tools, upper right. Others in the same situation might then get a fix from your efforts. Well done. :)

ps: just wanted to add - that rocks!

---

