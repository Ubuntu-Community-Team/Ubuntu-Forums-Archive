---
title: "128 bit wep encription crashes ubuntu"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by msmithy12 on 2007-06-05
ok so heres my network settings as showns by windows XP

Router Wireless Security Information

SSID:LYNKSYS
CHANNEL:11
ENCRYPTION:WEP(128 Bit)
PASSPHRASE:woodleabank
KEY:b3a83fb1494804215b2e88fb1c

everytime i put this is ubuntu it wont connect and when i change it from open source to shared key it crashes

i dont know if i should change it from open source to shared key but eaither way it dont work

Can Some1 help me please????
Thanx Matt

---

### Post by chili555 on 2007-06-05
Where are you putting: PASSPHRASE:woodleabank? I do not believe Linux needs a passphrase for WEP. Mine sure doesn't. Also WEP will not connect if you use LYNKSYS and the actual ESSID is linksys. You can verify the ESSID the router is broadcasting with:```
sudo iwlist eth1 scan
```Scan may take a few tries.

Connecting should be as easy as:```
sudo iwconfig eth1 essid LYNKSYS
sudo iwconfig eth1 key b3a83fb1494804215b2e88fb1c
sudo dhclient eth1
```Substitute your interface here if it is not eth1.

---

### Post by msmithy12 on 2007-06-05
thanx 4 your help but i`ve sorted the problem now

and it is 'lynksys' cos im a dyslexic moron and renamed my router

---

