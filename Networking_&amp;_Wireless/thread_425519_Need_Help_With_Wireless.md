---
title: "Need Help With Wireless"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by southcarolina_29709 on 2007-04-27
I just installed driver using ndiswrapper for my netgear ma521 everything went smooth shows driver is installed and hardware present,In network settings it's showing interface wlano is active but the link light is not coming on,I'm trying to get this by using dhcp because that's what i have always used with any linux distroIt seems that i'm close but have know idea where to start looking for the problem,I have search google but really have'nt found much to help me,So if anyone could help me get this up and running i would really appreciate it,Thanks

---

### Post by chili555 on 2007-04-27
Greetings from 29710! May we please see:```
iwconfig wlan0
sudo iwlist wlan0 scan
```Scan may take a few tries. Thanks.

---

### Post by southcarolina_29709 on 2007-04-28
root@ubuntu:/home/tim# iwconfig wlan0
wlan0          IEEE  802.11b   ESSID:off/any
                    Mode:Auto    Frequency:2.412  GHz   Access  Point: 00:00:00:00:00:00
                    Bit  Rate : 11  Mb/s   Tx-Power:20 dBm    Sensitivity=0/3 
                    RTS thr :2432 B    Fragment thr :2432  B
                    Encryption  key :off
                    Power Management :off
                    Link  Qaulity :100/100  Signal level : -95 dBm   Noise  Level:-256  dBm
                    Rx  invalid  nwid:0   Rx  invalid crypt :0  Rx  invalid  frag:0
                    Tx  excessive  retries :0    Invalid  misc :0   Missed  beacon :0

sudo iwlist wlan0 scan 
wlan0   no scan results   I tried the scan about 10 times same results

---

### Post by chili555 on 2007-04-28
Do you want the easy part or the hard part? The easy part is that connecting should be as easy as:```
sudo iwconfig wlan0 essid <essid_of_your_router>
sudo dhclient wlan0
```The hard part is, without scanning results, you don't know the exact name your router or access point is broadcasting, or if it is broadcasting at all.

You can get into the administration page of your router and make careful note of the ESSID and any encryption details. Remember, in ESSID's, linksys is not Linksys is not LINKSYS.

Try the commands above when you have the ESSID. If you have encryption, let us know if it's WEP, WPA or otherwise, and we'll proceed.

---

### Post by southcarolina_29709 on 2007-04-29
When i do sudo dhclient wlan0 when it gets through it's showing no dhcpoffers no working leases in persistent database-sleeping,i checked my router encryption is WEP

---

### Post by chili555 on 2007-04-29
It will not connect without the encryption details. Try this:```
sudo iwconfig wlan0 essid <essid_of_your_router>
sudo iwconfig wlan0 key <your_wep_key>
sudo dhclient wlan0
```If your key is ASCII instead of hex, prefix your key with s:  like this:```
sudo iwconfig wlan0 key s:myasciikey
```

---

### Post by southcarolina_29709 on 2007-04-29
Still the same,Is there anything else to try or should i purchase another card,if i need to get another card what should i get that's not a hassel to get going

---

### Post by chili555 on 2007-04-30
I think your card is fine, I wouldn't ditch it quite yet, If you do, throw it west!

Let's take a look at your WEP key. How many characters does it have? That will help us know if it's hex or ASCII. If the WEP key has letters, please put them in iwconfig in lower case, like this:```
sudo iwconfig wlan0 key 1234efgh67
```

Also, sometimes, WEP will respond better with the word 'open' or 'restricted' after the key. Try both:```
sudo iwconfig wlano key 1234efgh67 open
sudo dhclient wlano
```Then try the same with 'restricted.'

---

