---
title: "Card detected, got an IP, but no connectivity..."
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by irishbear on 2006-09-15
Howdy,

I've got an IBM Thinkpad T40 with a built in wireless card. I have Ubuntu 6.06 installed. My AP is a Belkin Wireless G ADSL router modem.

Ubuntu has detected my wireless card (ath0), and after I had added it's MAC to the MAC-filtering on my router, it picked up an IP address via DHCP just fine. However, beyond that I'm getting nothing - I can't even ping the router.

Here's some troubleshooting stuff:

```
lspci:
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)
```

```
iwconfig:
ath0      IEEE 802.11b  ESSID:"Bearcave"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:F1:FF:72:C2
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/94  Signal level=-48 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:05:4E:41:82:80
          inet addr:192.168.2.16  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe41:8280/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:730 (730.0 b)  TX bytes:3966 (3.8 KiB)
          Interrupt:11 Memory:f8ac0000-f8ad0000
```

```
johnbear@IT-JMELLER4:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:30:F1:FF:72:C2
                    ESSID:"Bearcave"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/94  Signal level=-49 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
```

```
johnbear@IT-JMELLER4:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:05:4e:41:82:80
Sending on   LPF/ath0/00:05:4e:41:82:80
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.16 -- renewal in 33865 seconds.
```

Anyone got any ideas?

---

### Post by NetworkGuy on 2006-09-15
>  IEEE 802.11b  

Is your access point 802.11b only.  Your iwconfig reports your ath0 as only an 802.11b, yet you say it's a g. (I believe you).

Possibly you have a driver that isn't quite right for your card.  I'm checking the forum but not finding the solution right now.  Check the forum your model card (AR5211) and see if you can find the right fix.  Also the wiki may help you out.

---

### Post by irishbear on 2006-09-15
> **NetworkGuy said:**
> Is your access point 802.11b only.  Your iwconfig reports your ath0 as only an 802.11b, yet you say it's a g. (I believe you).

I have my router set to operate in "Mixed Mode (b + g)", which *should* mean it'll accept connections from either 802.11b or 802.11g devices.

I'm still hunting on various forums for hints, but I didn't check the wiki yet - thanks :)

---

### Post by irishbear on 2006-09-16
OK, starting to zero-in on this one...

I can configure my router to transmit in "11g Only", "11b Only" or "Mixed (11b + 11g)". The T40 has an 802.11b card in it. If I set the router to 11b, bing! - suddenly everything works peachy.

If I set the router to "11g Only", the T40 *still* picks up an IP address just fine, but after that it receives no more communication.

So it looks like when the router is set to "Mixed (11b + 11g)" mode, the T40 establishes the connection using 11g, even though the card only physically supports up to 11b.

Is there a way to force Ubuntu to only connect using 11b?

Cheers!

John

---

### Post by irishbear on 2006-09-16
Sorted!

I downloaded and installed the latest version of the madwifi-ng drivers, and after a reboot, wireless is now working with the router set to Mixed mode! :KS

I followed a combination of the information on these three pages:

General Ubuntu madwifi installation instructions:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Hints on getting kernal sources installed for build step:
[http://www.mythtv.org/wiki/index.php/Ubuntu_Installation](http://www.mythtv.org/wiki/index.php/Ubuntu_Installation)
[http://www.linuxforums.org/forum/mandriva-linux-help/61178-wireless-2.html](http://www.linuxforums.org/forum/mandriva-linux-help/61178-wireless-2.html)

Hope this helps other people out there :D


John

---

