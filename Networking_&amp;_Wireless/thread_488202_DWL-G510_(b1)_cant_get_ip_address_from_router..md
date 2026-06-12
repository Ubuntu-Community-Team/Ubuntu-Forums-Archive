---
title: "DWL-G510 (b1) cant get ip address from router."
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by asch246 on 2007-06-29
Hi all,
I´m a bit of a newbie, I just installed a DWL-G510 pci wireless card (it´s hardware version b1 firmware version 4.10) and installed madwifi (not realising that it is already in restricted drivers). 
All appears to have gone well, until I try to get a ip using dhcp. 
I´ve been using the instructions[ here]("http://ubuntuforums.org/showthread.php?t=485579&") and [here]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo").
When I put in ¨dhclient ath0¨ this is the result:

```
root@xubuntu:/home/admin# dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 5297
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:e5:45:2c
Sending on   LPF/ath0/00:11:95:e5:45:2c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@xubuntu:/home/admin# 

```

I´m using WEP encryption on the network (64 -bit HEX) and the router is a DI-524. The network name is ¨dlink¨
The computer also has a ethernet card installed (which is what I am using currently, so I can paste terminal results here). 
I´m running Xubuntu 7.04 (fiesty Fawn), installed from the alternate i386 disc (due to the machine not having enough RAM for the normal ubuntu install)

Any help would be greatly appreciated!
Thankyou for your time.

---

### Post by Bachstelze on 2007-06-29
Did you configure your ESSID and WEP key correctly ? Also, are you sure your router runs a DHCP server ?

---

### Post by asch246 on 2007-06-30
Hi HymnToLife,
I think I´ve configured the essid and wep key correctly.
 here´s the output of iwconfig:

```
root@xubuntu:/home/admin# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dlink"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:DD:24:1E   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:<MY WEP KEY>   Security mode:restricted
          Power Management:off
          Link Quality=59/94  Signal level=-36 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@xubuntu:/home/admin# 

```

It´s after I check this is all correct that I try dhclient ath0 and get rejected (see previous post)

The router is definately set to DHCP server. Another computer is working fine using DHCP with the same router. 

Any ideas?

---

### Post by jack_linux on 2007-08-23
I'm experiencing the exact same problem.  I've been through tons of wikis and how-tos, and still I can't seem to get an IP address.  I am using the same card (D-Link DWL-G510 rev. b ver4.10) as asch246.  I've tried madwifi, and ndiswrapper.  With madwifi (the default after installation), I am at least able to see the networks that are available, but alas, I cannot connect.  Any help would be much appreciated.  My guess is the madwifi driver isn't the EXACT one that this card (revison b) needs.  I would venture to guess that everybody with this card has the same problem.  If I left out any important info, please let me know.

iwconfig:

```
 jack@jack-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"superwoman"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:B3:35:F8:B7   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/94  Signal level=-46 dBm  Noise level=-95 dBm
          Rx invalid nwid:28844  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Here's the printout of dhclient:

```
jack@jack-desktop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:6f:2e:47
Sending on   LPF/ath0/00:13:46:6f:2e:47
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

In case this might help, here's the hardware info on the wireless card (via lshw):
```
*-network:0
                description: Wireless interface
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 1
                bus info: pci@02:01.0
                logical name: wifi0
                version: 01
                serial: 00:13:46:6f:2e:47
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:fe1f0000-fe1fffff irq:22
```

---

### Post by austonst on 2007-10-13
Sorry for reviving a 3 month old topic, but I'd really like to know if this problem was ever resolved. I've had the same problem for a long time now, and I'd really like to find a fix for it Has anyone found a fix for this?

---

### Post by asch246 on 2007-10-13
I still havent gotten the card to work. it's still in the machine, unused.
The closest I've come was using puppylinux v3.00 With that, I was able to get a ip and stuff, but couldnt actually browse etc. that was only the other day, so I may try again with puppy.
After a couple of hours, a more exp. friend was able to get to a similar postion in xubuntu, but no resolution. 

Basically, it's still an unresolved issue for me, but we've learned to live with the cables. :(
I haven't given up though! Post here if you make any progress!

---

