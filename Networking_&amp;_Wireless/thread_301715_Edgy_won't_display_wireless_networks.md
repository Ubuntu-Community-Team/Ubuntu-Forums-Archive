---
title: "Edgy won't display wireless networks"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by Meysys on 2006-11-17
I recently upgraded to edgy from a clean install of Dapper, and now I cannot see any wireless networks in range.

If I manually type the name of the network I'm trying to connect to it'll work just fine, but its annoying and I can't connect to networks I don't know the name of.

---

### Post by dbott67 on 2006-11-17
What is the output of **iwlist scanning**?
```
dbott@dapper:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:40:05:B2:YY:XX
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-48 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.
```

---

