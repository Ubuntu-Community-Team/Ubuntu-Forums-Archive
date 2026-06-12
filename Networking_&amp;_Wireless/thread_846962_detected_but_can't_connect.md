---
title: "detected but can't connect"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by ms.shams on 2008-07-02
Hi every one,

i buy a new toshiba satellite u405 s2830.
and before booting vista format it and install ubuntu hardy :D
but i have a big problem. ubuntu detects my wlan card. i get bellow line from lspci output:
```
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

```

and after configuration with ubuntu network-manager iwconfig command shows bellow:
```
wlan0     IEEE 802.11g  ESSID:"TW-NET"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:3B:77:67   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=78/100  Signal level=-66 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

and "iwlist wlan0 scan" says: No scan results

my problem is:
after boot my wlan doesn't work. when i configure it with dhcp it can;t get ip from dhcp server. and when i configure it with static ip doesn't work too. but after many times restarting network, it works randomly. in this network many laptops with same distro exist and work with our network successfully.
this is good to know that my laptop works with wired lan.

can youe help me please as soon as possible?

---

### Post by flaggh on 2008-07-02
I too was unable to get network manager to connect to the wireless network.  I installed Wicd and everthing worked fine after that!

[http://www.wicd.net/]("http://www.wicd.net/")

---

### Post by ms.shams on 2008-07-02
i use wicd too.
in wicd, when i refresh list, i can see our network. and when i click on connect, wicd says connected. but after this i still disconnect from network. and hasn't ping.

---

### Post by ms.shams on 2008-07-02
can anyone help me please? i can't connect to our network. :(

---

### Post by feistybill on 2008-07-15
> **ms.shams said:**
> my problem is: after boot my wlan doesn't work. when i configure it with dhcp it can;t get ip from dhcp server. and when i configure it with static ip doesn't work too. but after many times restarting network, it works randomly. in this network many laptops with same distro exist and work with our network successfully.

same problem here. i cannot connect to an OPEN wlan (in windows it works), but i can connect to my other wlan (a WPA).

---

