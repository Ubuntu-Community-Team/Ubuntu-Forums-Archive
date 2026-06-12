---
title: "Linksys wireless"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by gatoruss on 2007-03-05
Hi.  New to Ubuntu, and need help connecting to the internet via Ubuntu.  I origianlly posted this on the "beginers forum," but after surfing thru the forums, have decided I probably should have posted here (here is a link to my original post:  [http://www.ubuntuforums.org/showthread.php?t=376357]("http://www.ubuntuforums.org/showthread.php?t=376357") ).

The card I purchased was a linksys wmp54g, which is listed as a compatible wireless card. In fact, [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinks](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinks), indicates that it "works out of the box."

Also, my router is a linksys as well.

If I go to Admin>networking> I get a list of potential connections:

[LIST]
[*]wireless wlan0
[*]wireless master (or some similar name - not sure why there are 2 showing, as I only have one)
[*]wired
[*]modem (the machine has no modem (I removed it make room for the wireless card))
[/LIST]

I have tried entering the network info into properties for both wireless (not at the same time). The system tells me it is "changing configuration." But if I test it (by trying to open FireFox), I do not get an internet connection.

I have seen "stuff" on some Ubuntu pages suggesting that I should use "network manager," but there isn't any such animal on any of my menus.  Can't download it since I don't have an internet connection :( 

Any idea what I am missing? Thinking maybe, I should just go with some differnet wireless card?

P.S. My home network is a secure network (WMP, I believe), so I have a SSID (note, in Admin>networking> info calls foe ESSID" rather than "SSID," not sure if this intended to be the same) and a passphase (password).

---

### Post by ncappel1 on 2007-03-05
If you see that the wireless connection is in the "networking" dialogue, (which is the reincarnation of the "network settings") then you have all the drivers ready and rearing to go. 

through the terminal, the output of
```
iwconfig
```
and 
```
ifconfig
```

should read something similar to this:

```
nicola@ithaca:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"212 Giles #9"  
          Mode:Managed  Frequency=2.412 GHz Access Point: 00:11:50:57:9B:EF   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=47/100  Signal level=-66 dBm  Noise level:-200 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
 and
```
nicola@ithaca:~$ ifconfig
ra0       Link encap:Ethernet  HWaddr 00:12:17:82:3D:DE  
          [b]inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST[/B]  MTU:1500  Metric:1
          RX packets:58182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47697 errors:1934 dropped:1934 overruns:0 carrier:0
          collisions:7646 txqueuelen:1000 
          RX bytes:80901535 (77.1 MiB)  TX bytes:5067051 (4.8 MiB)
          Interrupt:11 Base address:0xc000 

```

my wireless does the same thing, I can't use it unless I activate it each time I boot the machine.

---

### Post by gatoruss on 2007-03-05
What do I do to "Activate it"?

---

### Post by RomeReactor on 2007-03-05
Hi gatoruss. I suggest you disable the wired interface in "System-->Administration-->Networking", as most of the time (in my experience) it conflicts with wifi connections; as for activating your wireless, try in a terminal

```
sudo ifdown wlan0
```

then

```
sudo ifup wlan0
```

if that doesn't seem to help, also do

```
sudo dhclient wlan0
```

Remember to disable the wired connection before doing all of this. Hope this helps.

---

### Post by gatoruss on 2007-03-05
Thanks, but still not working.

The command "sudo ifup wlan0."

It looks for a DNS, then tells me no DHCPoffers rec'd.

Same with "sudo dhclient wlan0."

BTW, under Admin>networking, in additon to the **wlan0** i also have a **wmaster0**.  Plus a modem and the wired card (both of whichj are diabled.

---

### Post by gatoruss on 2007-03-05
Well, I followed the tutorial in HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. ([http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539) ), and entered the information in my interfaces file EXACTLY,........................and...............IT WORKS!!!!!!!!!!!

This post if from my Wi connection thru Ubuntu!!!!!!!!

---

