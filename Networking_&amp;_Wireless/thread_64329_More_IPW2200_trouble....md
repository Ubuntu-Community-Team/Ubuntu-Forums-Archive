---
title: "More IPW2200 trouble..."
date: 2005-09-10
forum: Networking &amp; Wireless
---

### Post by BeachBum on 2005-09-10
Hey everyone,

Sorry for another IPW2200 problem, but I've searched and it seems my problem is unique.  Last week my wireless crapped out, after not being able to fix it, a fresh Ubuntu install was in order.

Used updatedb & locate for  ipw2200, ipw2*, ipw*, *.fw, and ieee80211* and removed all references outside of my home directory.

dmesg, lsmod give me the standard 3 lines for ipw2200 and ieee80211.

Modprobe gives no errors for both ipw2200 and ieee80211.

iwconfig shows everything, as if I'm disconnected, all my info is there, but it says unassociated, and the AP MAC addy is all 0's.  

I'm using the latest versions of the firmware (2.3), driver (1.0.6), and the ieee stuff (1.0.3).

/etc/network/interfaces is configured properly, as I copied it over from when wireless worked.

The funny thing is that I had wireless working fine for several months, then this week it crapped out, and the wifi LED on my T42 doesn't even light up anymore.  Works fine in Windoze.  

Any thoughts, as I sure dislike using Windoze?

EDIT: I'm using Hoary, 2.6.10-5-386 (removed 686 after reading somewhere on here ipw installed in 386's directories)

---

### Post by mlomker on 2005-09-10
If the light isn't on then it's powered off.  I'm assuming it is enabled properly in your BIOS.  Have you tried **iwconfig eth1 power on**.

---

### Post by BeachBum on 2005-09-10
[QUOTE=mlomker]If the light isn't on then it's powered off.  I'm assuming it is enabled properly in your BIOS.  Have you tried **iwconfig eth1 power on**.[/QUOTE]

Yea, but unfortunately "power" is for power management, so I set that to off.

Here are various outputs:

root@localhost:~# iwconfig eth1
eth1      unassociated  ESSID:"BeachNet"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxx-xxxx-xx   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@localhost:~# iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:10:E1:CD:F5
                    ESSID:"BeachNet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=56/100  Signal level=-67 dBm
                    Extra: Last beacon: 131ms ago

root@localhost:~# lsmod | grep ipw2200
ipw2200               162568  0
firmware_class          9728  1 ipw2200
ieee80211              28900  1 ipw2200
ieee80211_crypt         6472  2 ipw2200,ieee80211

root@localhost:~# dmesg | grep ipw2200
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

root@localhost:~# lsmod | grep ieee80211
ieee80211              28900  1 ipw2200
ieee80211_crypt         6472  2 ipw2200,ieee80211

oot@localhost:~# dmesg | grep ieee80211
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, 1.0.3
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, 1.0.3
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

->As you can see, iwlist comes up with my AP, but the power LED is still off and I still cannot connect.  Weird, isn't it? :-k

---

### Post by mlomker on 2005-09-11
[QUOTE=BeachBum]Yea, but unfortunately "power" is for power management, so I set that to off.[/quote]

Oops, I gave it a shot.   ](*,) 

Normally you'd get a "Radio Frequency Kill Switch is On" message in dmesg if it were software disabled.  Ran across this, in case you need it. [RF Killswitch project](http://rfswitch.sourceforge.net/)

Have you tried disabling WEP on your access point as a test?  It could be something as simple as the WEP key.

---

