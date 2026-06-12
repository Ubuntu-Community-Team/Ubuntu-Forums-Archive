---
title: "WiFi card not scanning any networks"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by Javote on 2008-02-08
Hello. I just installed Ubuntu 7.10 for the first time, and everything works great, except my 802.11 card. I'm using a Dell Inspiron 8500 laptop, with a Truemobibe 1300 MiniPCI card (broadcom 4306 chip).

Right after install, I authorized the restricted drivers, but I still wasnt able to connect to my network. I tried using ndiswrapper, and i still cant find any networks (my other laptops are able to find around 6 near-by networks).

iwconfig shows:> eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And iwlist eth1 scan shows "no scan results". 

I tried manual configuration, but it wont work either, for testing purposes I have SSID broadcasting turned on.

Anyone knows what could be going on, or where else I should be looking at?

On a side note: no idea why it shows my interface as eth1 instead of wlan :confused:

PS: pardon my noobness

---

### Post by Hightide on 2008-02-09
Hi Javote

It seems the problem is the wireless is not associated with the router as it states..

** Access Point: Not-Associated **

Have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188"). It may help

regards

:)

---

