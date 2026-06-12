---
title: "Wireless is way slow (intel 3945)"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by Rotarychainsaw on 2007-08-28
Hey all,
I have a problem of my notebook wireless being very slow, I have searched for some answers on here but I think my problems may be different... The main problem is that I installed gutsy and moved to a new house in the same day so I'm not sure what the source of the problem is.

In my new house I am leaching wireless off of my school. I'm pretty far away but I am getting a signal. My big computer get less signal with better wireless speeds... I'm trying to figure out if this speed problem is related to the distance or if it's a gutsy problem. I'll probably walk down to the library later for some high signal testing. 

one thing I noticed is that in iwconfig it knows that the network is 802.11g, but the connection speed is listed as 11mbs or even 2mbs sometimes. Invalid misc is through the roof, and signal level and noise level don't seem to be too bad(~ -75db). 

Please advise, thanks!

edit - I should add that network manager seems to be reconnecting rather a lot.

---

### Post by jnorthr on 2007-08-28
almost the same problems here with a similar config. Invalid misc. is thru the roof, speeds vary from 5.5mb up to 54mb depending on where my linksys wireless-G usb device is located. I know there is another wireless wep-protected user near here, so i am wondering if my system is confused as to which one to listen or the signal from the other user makes mine fade.

---

### Post by CyborgMax on 2007-09-04
Hello, i can confirm this too.

laptop:
- new DELL Inspiron 6400
- Intel PRO/Wireless 3945
- Intel Pentium Dual-Core CPU
- distro: ubuntu Feisty
- kernel 2.6.20-16-generic

windows: wlan working.

i don't think that the wlan-router (Vigor2500) because with other notebooks (intel wlan too, feisty too) i can connect without any problems.

ethernet is fully working.

reinstalling feisty did'n work. also live CD - same issue.

connecting with network-manager really a problem. also without WEP. Always i can see the aviable wireless networks (also mine) in the network-manager-applet (with great signal) but only in 1 of 12 cases i can connect. and then the connection is very very slow.

I tried manual configuration, without natwork-manager and with static IPs. Since then connecting is now Problem. But the connection is very very slow, too.

iwconfig eth1:
```
eth1 IEEE 802.11b ESSID:"Vigor2500"
          Mode:Managed Frequency:2.437 GHz Access Point: 00:90:4B:1A:6E:CC
          Bit Rate:11 Mb/s Tx-Power:15 dBm
          Retry limit:15 RTS thr:off Fragment thr:off
          Power Management:off
          Link Quality=66/100 Signal level=-68 dBm Noise level=-68 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:3051 Missed beacon:0
```

ipw3945:
```
filename: /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license: GPL
author: Copyright(c) 2003-2006 Intel Corporation
version: 1.2.0mp
description: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion: 9B03103B15A8FE1824967C2
alias: pci:v00008086d00004227sv*sd*bc*sc*i*
alias: pci:v00008086d00004222sv*sd*bc*sc*i*
depends: ieee80211
vermagic: 2.6.20-16-generic SMP mod_unload 586
parm: antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm: disable:manually disable the radio (default 0 [radio on]) (int)
parm: associate:auto associate when scanning (default 0 off) (int)
parm: auto_create:auto create adhoc network (default 1 on) (int)
parm: led:enable led control (default 1 on)
 (int)
parm: channel:channel to limit associate to (default 0 [ANY]) (int)
parm: rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm: mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
```

"sudo iwpriv eth1 set_mode 4" does not work or change anysthing.

hoping for some help.

regards,
max

---

