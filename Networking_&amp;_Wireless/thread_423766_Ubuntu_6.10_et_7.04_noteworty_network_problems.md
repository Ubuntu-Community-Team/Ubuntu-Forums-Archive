---
title: "Ubuntu 6.10 et 7.04 noteworty network problems"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by eiapoce on 2007-04-26
I am somehow a newbie. Can't pass my days in front of the pc configuring linux. I just write this post to ask about my problem with ubuntu.

First problem: If I start the machine while not connected with the cable I don't get internet. I use a router with DHCP, so it should be easy: plug the cable, get IP, surf. It's not this way. 

I start the laptop, then when I dock it at the table and plug the cable, nothing happens! Also opening the network manager (System / Administration / Network Tools) I cant bring the ehternet to work... If I start the laptop with the cable plugged then internet is fine. I would say this is a serious bug from the user point of view. Since windows2000 (98?) microsoft provides autoconfig for the network, the name for the technology is as you know plug&play...

Is there a way to have the network recognize the cable insertion and start the DHCP client right away? And if there is this method anyone knows why it's not implemented by default? 

Second Problem: The wireless, or lack of! I have this AP now configured for WEP (since I understood that WAP would be more difficult for linux) Well... even if in Feisty I can get the network manager to discover my network name I can't connect to it! After supplying the password everything stays there and nothing happens... no wireless... In 6.10 the situation is worse since it can't even detect the network.

Any help gretly appreciated.

My config is: 

Turion64 on ATI 200M - Wireless Ralink2500 (suggested by the free software foundation) - Integrated Wired Connection - HD100Gb partitioned WinXP home + Ubuntu 6.10 (because of infamous xorg bug with 200m)

Router Dlink 604T running Australian FirmWare2.xx

---

### Post by dolphin_oracle on 2007-04-26
I don't know about automatically upon insertion, but you can try these commands after plugging in your network cable.

sudo ifconfig eth0 up
sudo dhclient eth0

---

### Post by eiapoce on 2007-04-26
> **dolphin_oracle said:**
> I
sudo dhclient eth0

Thanx, I tried the command already without success. 

I found that using the network manager and selecting deactivation and then activation the wired net goes online. A still too cumbersome option by my personal point of view.

For the wireless I am now hopeless... and still think that there is something plainly wrong, since it works for KISMET why does't work normally... for the technically experts I dump here the results of the iwconfig command:

```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"xxxxx"  
          Mode:Monitor  Frequency=2.442 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-65 dBm  Noise level:-207 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

and ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:40:D0:8C:A5:51  
          inet addr:192.168.69.2  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe8c:a551/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2714638 (2.5 MiB)  TX bytes:966181 (943.5 KiB)
          Interrupt:201 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104600 (102.1 KiB)  TX bytes:104600 (102.1 KiB)

ra0       Link encap:UNSPEC  HWaddr 00-10-60-AF-06-02-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:591454 (577.5 KiB)
          Interrupt:185 Base address:0x4000 

```

---

### Post by roaldz on 2007-04-26
Your iwconfig output displays "Mode:Monitor".
I read you've used Kismet. Kismet needs to put your wlan interface (ra0) into monitor mode, in order to work. If you'd try this
```

sudo iwconfig ra0 mode managed

```
Your wlan interface will turn to "managed" mode, this is needed to connect to a network properly.
Now you may try to get it online:
```

sudo ifup ra0
sudo dhclient ra0

```

---

### Post by eiapoce on 2007-04-26
[QUOTE=roaldz;2540295]Your iwconfig output displays "Mode:Monitor".
I read you've used Kismet. Kismet needs to put your wlan interface (ra0) into monitor mode, in order to work. If you'd try this
```

sudo iwconfig ra0 mode managed

```
Your wlan interface will turn to "managed" mode, this is needed to connect to a network properly.
[/QUOTE=roaldz;2540295]

Thanks for the help, much appreciated. Unfortunately even in monitor mode it is not responding properly to the network manager. going to give up soon, looks like the cable is the reliabe way?

I just noticed that randomly clicking in the network manager can start and stop the card from working ...when I say randomly I mean it, if I am gonna do that on porpouse there is no way to attain the same resoults 

Enrico

---

### Post by SwaroopKunduru on 2007-04-26
> **dolphin_oracle said:**
> I don't know about automatically upon insertion, but you can try these commands after plugging in your network cable.

sudo ifconfig eth0 up
sudo dhclient eth0

I did this and have a problem. Please see the attachment.

Regards,

Swaroop Kunduru.

---

### Post by eiapoce on 2007-04-27
if you do this:
```
sudo dhclient eth0

```

AND you are connected to the network then you get this:

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:40:d0:8c:a5:51
Sending on   LPF/eth0/00:40:d0:8c:a5:51
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.69.100
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.69.100
bound to 192.168.69.2 -- renewal in 1354 seconds.

```

I found the way to have the bugshit (Networkmanager) to connect to the wired ethernet, it goes like this:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

And then after a while the network manager realizes that there is actually a cable and assigns a IP. Wireless is still not working.

Enrico

---

