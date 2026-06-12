---
title: "Wireless connection dropped after switching router - Lubuntu"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by pedroso on 2014-01-11
I recently switched to a new router, and my wireless has stopped connecting. I can connect fine from other computers, as well as with cable. I can see the wireless access points from the drop-down list on the menu. But when I enter the password nothing happens. I am wondering what I am doing wrong, and if I have to set it up manually, but I don't know the commands to do that. I'm using Lubuntu 12.10 on an IBM Thinkpad T42.

This is the result from "iwconfig":

eth1       unassociated   ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"   Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is the result from "sudo iwlist eth1 scan"

 Cell 04 - Address: 7C:03:4C: OB:65:A7
                    ESSID:"HomeBox-65A1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:62  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 916ms ago

---

### Post by praseodym on 2014-01-11
Is it a "hidden" network? If yes, broadcast the ESSID

---

### Post by pedroso on 2014-01-11
It isn't hidden, I can see it but not connect to it.

---

### Post by chili555 on 2014-01-11
Does your ipw2100 do WPA2? Some don't.```
sudo iwlist eth1 auth
```

---

### Post by pedroso on 2014-01-19
Yes. WPA and WPA2

---

### Post by praseodym on 2014-01-19
Check also "iwlist chan". If the channel is set to "auto", maybe the driver only has 11 and the router broadcasts on 12 or 13?! If so, set a fixed channel.

---

