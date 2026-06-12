---
title: "HELp need for bcm4318 Apple (ppc) setup"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by Kasa on 2008-03-22
Basicly I have been following the setup here: [http://ubuntuforums.org/showpost.php?p=899926&postcount=24](http://ubuntuforums.org/showpost.php?p=899926&postcount=24)

I get up to 
```
iwlist eth1 scan
```

which every time comes back with 
no scan result.

I did try the [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
before seeing that forum topic.
I am unsure no how to get this to pick up my current wireless network (i ensured the 11mbs has been set on the wireless network but still not pickup)

does anyone have any help for me 

I am also runing A PPC Dapper.

---

### Post by Kasa on 2008-03-22
not sure if this can help.
```
 sudo iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:60:64:1C:C5:AE
          Bit Rate:11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Kasa on 2008-03-22
I got it to show the Network on 
iwlist scan

but how do I make it connect to it and stay connected :? ?

---

