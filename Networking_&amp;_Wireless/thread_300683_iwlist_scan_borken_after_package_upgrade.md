---
title: "iwlist scan borken after package upgrade"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by trubblemaker on 2006-11-16
I recently upgraded my dhcp package, just doing a normal update, now 
```
iwlist scan
```
only shows the first results:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:34:ED:E9:20
                    ESSID:"ubc"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

There are more networks! I know 'cause if I change my essid to another one that used to be there, I can connect and get a new ip.  there just not showing up in iwlist scan:


```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:34:ED:E9:20
                    ESSID:"ubc"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

meat@troublemaker:~/Desktop$ sudo iwconfig wlan0 essid any
meat@troublemaker:~/Desktop$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:34:F2:07:75
                    ESSID:"FatPort (Non-UBC user)"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

---

### Post by trubblemaker on 2006-11-20
should have mentioned that I'm using ndiswrapper and bcmwl5 driver.

---

### Post by spd106 on 2006-11-21
I'm not sure that this is the answer, but I remember reading somewhere that iwlist will only give you the cached results when run as a unprivileged user. So you have to run it as root (sudo) to get it to generate a new scan.

---

### Post by trubblemaker on 2006-11-21
how right you are.  I had a script that used to do that on boot, but I recently removed it.  Thanks your totally right.  Now I'm back on the good road.

---

