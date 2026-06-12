---
title: "Atheros minipci wireless card can find access points but cannot connect"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by netranger on 2008-09-07
Hi guys

i'm using (from lspci),

00:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

	Subsystem: Atheros Communications Inc. Compex Wireless 802.11 b/g  MiniPCI Adapter, Rev A1 [WLM54G]

and the madwifi-hal-0.10.5.6 drivers. since installing those drivers i can see all access points in range but I cannot connect to one. i've turned security off on mine to see if that was the problem but that doesn't work either. here is some output from the usual commands to help.

# lshw -C network

  *-network:0             

       description: Wireless interface

       product: AR2413 802.11bg NIC

       vendor: Atheros Communications Inc.

       physical id: 6

       bus info: pci@0000:00:06.0

       logical name: wifi0

       version: 01

       serial: 00:c0:a8:bc:67:cd

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

# wlanconfig ath0 list scan

SSID            BSSID              CHAN RATE  S:N   INT CAPS

SKY10719        00:1b:2f:6d:b3:24    1   54M 55:0   100 EPSs WPA WME ATH

SKY08192        00:18:4d:6a:9f:00   11   54M 20:0   100 EPSs WPA WME ATH

TalkTalk4j59c   00:1b:9e:e2:cf:53   12   54M 12:0   100 EPs

# ifconfig

ath0      Link encap:Ethernet  HWaddr 00:c0:a8:bc:67:cd  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



eth0      Link encap:Ethernet  HWaddr 00:14:0b:00:90:76  

          inet addr:192.168.38.3  Bcast:192.168.38.255  Mask:255.255.255.0

          inet6 addr: fe80::214:bff:fe00:9076/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:112125 errors:0 dropped:0 overruns:0 frame:0

          TX packets:74788 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:9248410 (8.8 MB)  TX bytes:5879576 (5.6 MB)

          Interrupt:18 Base address:0x400 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2266 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2266 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:115252 (112.5 KB)  TX bytes:115252 (112.5 KB)



wifi0     Link encap:UNSPEC  HWaddr 00-C0-A8-BC-67-CD-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1054076 errors:0 dropped:0 overruns:0 frame:10961

          TX packets:27004 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:280 

          RX bytes:146853328 (140.0 MB)  TX bytes:1888060 (1.8 MB)

          Interrupt:19

# iwconfig 

lo        no wireless extensions.



eth0      no wireless extensions.



wifi0     no wireless extensions.



ath0      IEEE 802.11g  ESSID:""  Nickname:""

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  

          Retry:off   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=57/70  Signal level=-39 dBm  Noise level=-96 dBm

          Rx invalid nwid:24129  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# uname -r

2.6.24-21-generic

I can see the wireless access points via the gnome interface on my desktop and selecting my one just sends that into a loop but it never actually connects. my router has no MAC access restrictions and is currently using WEP-PSK security though as said i've also tried with no security. The ESSID is broadcast as "SKY10719" currently also and is definately picked up.

Any help would be much appreciated.

---

### Post by netranger on 2008-09-07
*bump*

---

### Post by netranger on 2008-09-07
*bump*

---

### Post by netranger on 2008-09-08
*bump*

---

### Post by netranger on 2008-09-09
*bump*

---

### Post by netranger on 2008-09-13
*bump*

---

### Post by RavUn on 2008-09-14
*bump* for me too.

---

### Post by Crafty Kisses on 2008-09-14
Well let's see if it's actually detected, try the following:
```
sudo pccardctl ident
```
Hopefully you get an output similar to this:
```
Socket 0:
    product info: "Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN Reference Card", "00"
    manfid: 0x0271, 0x0012
    function: 6 (network)
```

If you get no output then the memory on the card cannot be read. Now we need to open a configuration file and add this information to it:
```
gksudo gedit /etc/pcmcia/config.opts
```
The information needs to look similar like this, **but substitute your own information**:
```
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"
```
After making the changes above, you need to do the following:
```
 sudo kill -HUP `cat /var/run/cardmgr.pid'
```
Then run this following command to see if the card is recognized:
```
lshw
lshw -C network
```
See if that brings the card alive.

---

### Post by RavUn on 2008-09-14
Would that work with the Broadcom BCM4312 do you know?  There's no output for ```
sudo pccardctl ident 
```
If so, I don't know what all I'd need to add.

It's so irritating since it was working right before the updates.  I waited a while and switched back to Ubuntu to try again and it connected right away but it was to the wrong network so I tried to switch to my wireless and it would not connect... I tried the other one again and it didn't work, either.  I connect fine when I'm running Vista on this laptop.

EDIT: I just tried WICD and it does the same thing.  It says "Obtaining IP address" for a while then stops and does not connect.  I tried connecting wired and it connects but the internet does not work.

---

### Post by netranger on 2008-09-15
> **Codename said:**
> Well let's see if it's actually detected, try the following:
```
sudo pccardctl ident
```
Hopefully you get an output similar to this:
```
Socket 0:
    product info: "Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN Reference Card", "00"
    manfid: 0x0271, 0x0012
    function: 6 (network)
```

If you get no output then the memory on the card cannot be read. Now we need to open a configuration file and add this information to it:
```
gksudo gedit /etc/pcmcia/config.opts
```
The information needs to look similar like this, **but substitute your own information**:
```
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"
```
After making the changes above, you need to do the following:
```
 sudo kill -HUP `cat /var/run/cardmgr.pid'
```
Then run this following command to see if the card is recognized:
```
lshw
lshw -C network
```
See if that brings the card alive.

Thanks for this. I ran the

```
pccardctl
```

command and received no output. What options do I have now?

The ```
/etc/pcmcia/config.opts
``` file exists but has nothing resembling the output you suggest I add there. Should I add an entry here anyway? If so how do I get my specific values?

The file ```
/var/run/cardmgr.pid
``` doesn't exist for me, is there something I need to install or run?


Thanks again for your help :)

---

### Post by Crafty Kisses on 2008-09-18
Not sure if you have done this yet, but install this package:
```
sudo apt-get install madwifi-tools
```

---

### Post by netranger on 2008-09-18
i have this installed currently, as near as i can tell it provides the following utilities:

athchans
athctrl
athdebug
ath_info
athkey
athstats

---

### Post by netranger on 2008-09-27
do you have any other advice on this as it still wont work for me :(

---

