---
title: "Intel 4965 AGN WPA Enterprise trouble"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by AndyCee on 2008-08-29
Heya.

My Intel 4965agn wireless network card works beautifully at home, where I have WPA2 PSK encryption, but won't connect to the network at uni which uses WPA Enterprise (with a hidden SSID).

Once i've entered the network settings, it sees the network but won't authenticate. I'm using the nm-applet, which has worked fine in the past (with my old laptop).

The relevant output of dmesg is:
```
[ 6936.452875] wlan0: deauthenticate(reason=3)
[ 6945.025151] wlan0: Initial auth_alg=0
[ 6945.025159] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 6945.083748] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 6945.083754] wlan0: authenticated
[ 6945.083759] wlan0: associate with AP 00:0d:bc:50:67:12
[ 6945.273055] wlan0: RX AssocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=192)
[ 6945.273061] wlan0: associated
[ 6945.277474] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6955.539556] wlan0: no IPv6 routers present
[ 6975.209024] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=23)
[ 6975.209030] wlan0: deauthenticated
[ 6976.204394] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 6976.206209] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 6976.206216] wlan0: authenticated
[ 6976.206220] wlan0: associate with AP 00:0d:bc:50:67:12
[ 6976.208996] wlan0: authentication frame received from 00:0d:bc:50:67:12, but not in authenticate state - ignored
[ 6976.211873] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=193)
[ 6976.211878] wlan0: associated
[ 6977.670307] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=23)
[ 6977.670314] wlan0: deauthenticated
[ 6977.685544] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=2)
[ 6978.062395] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=2)
[ 6979.060043] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 6979.062759] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 6979.062765] wlan0: authenticated
[ 6979.062769] wlan0: associate with AP 00:0d:bc:50:67:12
[ 6979.066280] wlan0: authentication frame received from 00:0d:bc:50:67:12, but not in authenticate state - ignored
[ 6979.071445] wlan0: authentication frame received from 00:0d:bc:50:67:12, but not in authenticate state - ignored
[ 6979.075383] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=194)
[ 6979.075388] wlan0: associated
[ 6996.420218] wlan0: Initial auth_alg=0
[ 6996.420230] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 6996.423720] wlan0: Initial auth_alg=0
[ 6996.423728] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 6996.423747] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=256 status=12)
[ 6996.423752] wlan0: unexpected authentication frame (alg=0 transaction=256)
[ 6996.425358] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 6996.425363] wlan0: authenticated
[ 6996.425368] wlan0: associate with AP 00:0d:bc:50:67:12
[ 6996.427882] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=195)
[ 6996.427887] wlan0: associated
[ 7024.772498] wlan0: deauthenticate(reason=3)
[ 7040.593494] wlan0: Initial auth_alg=0
[ 7040.593502] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 7040.600319] wlan0: Initial auth_alg=0
[ 7040.600326] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 7040.604343] wlan0: Initial auth_alg=0
[ 7040.604350] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 7040.614693] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 7040.614700] wlan0: authenticated
[ 7040.614704] wlan0: associate with AP 00:0d:bc:50:67:12
[ 7040.729889] wlan0: authentication frame received from 00:0d:bc:50:67:12, but not in authenticate state - ignored
[ 7040.758367] wlan0: authentication frame received from 00:0d:bc:50:67:12, but not in authenticate state - ignored
[ 7040.772065] wlan0: authentication frame received from 00:0d:bc:50:67:12, but not in authenticate state - ignored
[ 7040.775092] wlan0: authentication frame received from 00:0d:bc:50:67:12, but not in authenticate state - ignored
[ 7040.785558] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=196)
[ 7040.785586] wlan0: associated
[ 7070.725503] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=23)
[ 7070.725510] wlan0: deauthenticated
[ 7071.720196] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 7071.723789] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 7071.723796] wlan0: authenticated
[ 7071.723801] wlan0: associate with AP 00:0d:bc:50:67:12
[ 7071.730755] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=197)
[ 7071.730760] wlan0: associated
[ 7095.899807] wlan0: deauthenticate(reason=3)
```

Any suggestions on how to approach this? Reading other threads suggests that the driver (iwl4965) is perhaps not finalised...

---

### Post by Crafty Kisses on 2008-08-29
Post the results of this command: ```
dmesg | grep iw
```

---

### Post by AndyCee on 2008-08-29
```
[   38.364677] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   38.364679] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   38.391805] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   39.765708] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   39.766716] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[ 7683.120693] iwl4965: Radio Frequency Kill Switch is On:
```

---

### Post by AndyCee on 2008-09-03
Hmmm..
seems to be working now...odd. Cool, but odd.

Thanks anywayz.

-AndyCee

---

### Post by AndyCee on 2008-09-03
Looks like I got too excited.

The network connected once. After re-entering my password & details multiple times.

In the nm-applet, it seems to indicate that I am currently (and seemingly always) connected to a wired network. I'm pretty sure I'm not, as there is no network cable attached...

This is my ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:40:d0:e8:91:ec  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294960187 overruns:0 frame:0
          TX packets:0 errors:0 dropped:536 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:40:d0:e8:91:ec  
          inet addr:169.254.11.121  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:218 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228684 (223.3 KB)  TX bytes:228684 (223.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:6a:12:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28599 (27.9 KB)  TX bytes:19575 (19.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-6A-12-F9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Any more thoughts please? Can someone suggest how to temporarily disable the ethernet to see if that's causing a problem?

---

### Post by AndyCee on 2008-09-09
WELL...

I had to do a fresh install anyway. The wireless connects after about 5 attempts on average. Not very impressed - especially as the phase2 and password box have to be re-entered every time.

Still, it works. It sees the network after about 6 seconds of entering my details. I'm not sure whether it's because the network has a hidden SSID (which causes enough problems for students) or because the network encryption is WPA Enterprise.

Oh well. Hopefully Intrepid will have some answers.

---

### Post by AndyCee on 2008-09-17
It's somehow managed to connect. Only took 14 or so attempts...

Here is the output of the last bunch of lines of dmesg:

```

[ 9669.078261] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=23)
[ 9669.078270] wlan0: deauthenticated
[ 9669.078277] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 9669.079900] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 9669.079910] wlan0: authenticated
[ 9669.079914] wlan0: associate with AP 00:0d:bc:50:67:12
[ 9669.082266] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=183)
[ 9669.082274] wlan0: associated
[ 9670.594745] wlan0: Initial auth_alg=0
[ 9670.594759] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 9670.596465] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=256 status=12)
[ 9670.596473] wlan0: unexpected authentication frame (alg=0 transaction=256)
[ 9670.791765] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 9670.793369] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 9670.793377] wlan0: authenticated
[ 9670.793381] wlan0: associate with AP 00:0d:bc:50:67:12
[ 9670.795751] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=184)
[ 9670.795758] wlan0: associated
[ 9704.308462] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=23)
[ 9704.308472] wlan0: deauthenticated
[ 9704.308488] wlan0: RX deauthentication from 00:0d:bc:50:67:12 (reason=2)
[ 9704.308496] wlan0: authenticate with AP 00:0d:bc:50:67:12
[ 9704.310169] wlan0: RX authentication from 00:0d:bc:50:67:12 (alg=0 transaction=2 status=0)
[ 9704.310176] wlan0: authenticated
[ 9704.310181] wlan0: associate with AP 00:0d:bc:50:67:12
[ 9704.312546] wlan0: RX ReassocResp from 00:0d:bc:50:67:12 (capab=0x431 status=0 aid=185)
[ 9704.312555] wlan0: associated
[ 9719.887535] wlan0: no IPv6 routers present
```

Seriously. I'm updating the kernel to 2.6.24-21 just in the hope there's some kind of fix included. Can anyone read why this isn't working? Or ideas for a different setup? The network manager retains all the needed details, but prompts for my password and the phase2 type (MSCHAP V2) every few minutes while my laptop is negotiating.

---

