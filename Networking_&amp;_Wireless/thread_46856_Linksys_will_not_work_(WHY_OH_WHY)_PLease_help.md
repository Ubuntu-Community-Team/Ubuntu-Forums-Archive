---
title: "Linksys will not work (WHY OH WHY) PLease help"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by drezman on 2005-07-06
Hello all
I'm new to this posting stuff :)
I have a linksys WPC54GS card with Ubuntu and it wont work ):
I finally got the ndis deal to load on startup so now the system can see the card in the network config but it will not find my network even after me giving all the info.  I checked the Kwifimanager and it doesn't help.  All it tells me is that is has full signal but wont find/display what network its getting it from.

So please if anyone has a fix for this, it would be best thing for me since slice bread

---

### Post by varunus on 2005-07-06
Can you give us some more info?  Go to the console and type

```
 sudo iwconfig
```

If you want to manually configure your wireless from a terminal, type
```
sudo iwconfig wlan0 essid <i>ssid of access point</i>
sudo dhclient wlan0
``` 

Those two commands will set up net access manually.  Ndiswrapper can't show signal strength, however, or at least it couldn't when I last used it...(I'm using the madwifi driver.)

---

### Post by drezman on 2005-07-07
Hola :)

This is whats in my iwconfig file
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

-----------------------------------------------------------------------------------------------------------
my ifconfig file when I have my ethernet connected 

eth0      Link encap:Ethernet  HWaddr 00:00:39:63:FC:A1
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe63:fca1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10555 errors:17 dropped:0 overruns:0 carrier:17
          collisions:0 txqueuelen:1000
          RX bytes:13601363 (12.9 MiB)  TX bytes:1370803 (1.3 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:398732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:115680267 (110.3 MiB)  TX bytes:115680267 (110.3 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:06:0B:26
          inet6 addr: fe80::212:17ff:fe06:b26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:10800000-10801fff

-------------------

I also tried to do the manual thing and it look like it was searching on some ports but then said nodhcp offers (thing like that)
I have the wireless security set to WPA (not sure if this has anything to do with this)

I feel like I'm learning how to use a computer all over again now that I'm trying to use linux :)

---

### Post by varunus on 2005-07-07
What do you see when you run "sudo iwlist wlan0 scanning"?

It seems you are not picking up any access points from your iwconfig output...

---

### Post by drezman on 2005-07-07
it says 

wlan0    No scan results


I changed me security to wep and it also didn't work, I turned off the security as well and it didn't work


I'm almost ready to burn the card.  Do you know any G cards that will plug and plag and with linux ?

---

### Post by drezman on 2005-07-11
Hey man, thanks for the help.  I got it work
turns out that was a driver problem.  found the right drivers and it work

---

