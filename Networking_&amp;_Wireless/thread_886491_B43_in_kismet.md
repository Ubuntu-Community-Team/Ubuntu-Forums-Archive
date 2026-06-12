---
title: "B43 in kismet"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by MarlonDean on 2008-08-11
Hey everyone,

I am trying to get Kismet to use my Broadcom wifi card. I enable the source as b43,wlan0,broadcom, but get the following error :Unknown capture source type 'b43' in source 'b43,wlan0,broadcom' I have checked numerous sites and many of them use this source, why wont it work for me? If i run iwconfig i get:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have been using Ubuntu 8.04 for only 3 weeks, so please have patience with me.

thanks in advance

---

### Post by cdtech on 2008-08-11
The Broadcom has no monitor mode. You can type:
```
iwconfig wlan0 mode monitor
```
and it will probably spit out an error such as:
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.
```

---

### Post by MarlonDean on 2008-08-11
Ok, so I wont be able to use Kisemt after all? I came across sites where people claim that you can use kismet with a broadcom, even a kismet manual i found said you can. Is there a work around for this? 

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

---

### Post by cdtech on 2008-08-11
I really haven't tried after I found out that I couldn't monitor with mine but it's been awhile. There may be a driver somewhere that has been developed that I'm not aware of.

---

### Post by atamakosi on 2008-08-23
I would be greatly interested to know if there is a fix or work around for this.  I'm having the same issues with my broadcom card and kismet.

---

### Post by kalmi on 2009-06-20
My b43 card works fine in monitor mode. The trick is to bring the card down first and set it to monitor mode and bring it back up.

---

### Post by kevdog on 2009-06-21
I can personally vouch for b43 along with kismet.  aircrack has some good tutorials.  You also need the iw program (which instructions can be found at aircrack and through google).

---

