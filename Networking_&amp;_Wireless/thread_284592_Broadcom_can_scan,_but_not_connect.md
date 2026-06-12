---
title: "Broadcom can scan, but not connect"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by Fuzzypants on 2006-10-25
I'm running Ubuntu 6.06 on an HP Pavilion 5500US with a Broadcom 4301 wireless network adapter.  I followed the instructions here: [http://ubuntuforums.org/showpost.php?p=752155&postcount=7](http://ubuntuforums.org/showpost.php?p=752155&postcount=7),  and I can scan for networks, and they all show up (encrypted and non), but I can't connect to either.

When I try through the "Network settings" window, it thinks for a minute, says it's connected, but isn't really connected to anything.  I don't get an IPv4 address, I can't see any of the other computers on the network, nothing.

All of the networks I've tried have been around -64dBm. (which is about right for a wireless network, right?).  If I try a static address, it doesn't wait for anything (so I'm pretty sure that's dhclient working in the background), and it gives me whatever IPv4 address I fed it, but I still can't see anyone else on the network.

Can anyone offer any advice?  Thanks.

[edit] Here's some console stuff:

al@fuzzypants:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:90:4B:42:37:45
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe42:3745/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d0002000-d0004000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:808 (808.0 b)  TX bytes:808 (808.0 b)

al@fuzzypants:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

al@fuzzypants:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:90:4b:42:37:45
Sending on   LPF/eth1/00:90:4b:42:37:45
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:9d:88:42:c8
Sending on   LPF/eth0/00:0d:9d:88:42:c8
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:90:4b:42:37:45
Sending on   LPF/eth1/00:90:4b:42:37:45
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
al@fuzzypants:~$

---

### Post by wieman01 on 2006-10-26
Does this give you any output?
> iwlist scan
If no scanning results, then there is a good chance that you have not installed the driver correctly.

---

### Post by Fuzzypants on 2006-10-26
Thanks for your quick reply.  'iwlist scan' scans and find all the local wireless networks correctly.  It's only when I actually try to connect to any of the networks that any problem surfaces.

```

al@fuzzypants:/media$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:09:2D:CA
                    ESSID:"SexMuffin77"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0D:88:88:2F:6F
                    ESSID:"Compound2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-62 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:17:31:FB:14:F1
                    ESSID:"Jarrett"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-92 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.




```

---

### Post by wieman01 on 2006-10-26
Yes, your problem is that your card tries connect on a different channel:
> Mode:Managed **[COLOR="Red"]Frequency:2.462[/COLOR]** GHz Access Point: Not-Associated
The networks run on channel 6 **[COLOR="Red"](Frequency:2.437 GHz)[/COLOR]** but not so your card. Try to change the channel on the router (1, 6, 11, others) and see if this helps.

---

### Post by Fuzzypants on 2006-10-26
Ouch.  Good eye.  Hm, my wireless router only seemed to support channel 6, so I issed:

```
iwconfig eth1 channel 6
```

And that seemed to get it set on the right frequency (at least it says it is), however, that seemed to fix nothing.  I get the same output from any of those commands, except 'iwconfig eth1' shows a Frequency of 2.437 GHz.

---

### Post by wieman01 on 2006-10-26
Ok, then we need to get our hands a bit dirty... Please tell me a bit more about your network: DHCP or Static IP, ESSID, Encryption, MAC filtering, etc.

Then show me the contents of this file please:
> sudo gedit /etc/network/interfaces

BTW: Please change the router's channel setting rather than your PC's. Worth a try.

---

### Post by Fuzzypants on 2006-10-26
My wireless router doesn't seem to support any channel value other than '6'.

I'm afraid I'm offsite now and can't get the exact network settings, I'll get them the next time I have access to them.

Another post I found around here suggested using dhcpcd rather than dhclient.  I'm going to try that once I can get the machine back on a network.

Thanks for you help thus far.

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2 
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by wieman01 on 2006-10-26
Ok, please update your "interfaces" file so that it looks like this (replace the contents):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid **[COLOR="Red"]your_essid[/COLOR]**
Replace **[COLOR="Red"]your_essid[/COLOR]** with the name of your network (no "" necessary).

Then restart the network:
> sudo ifdown eth1
> sudo ifup eth1

---

### Post by Stephen_at on 2006-10-26
I had to change the wireless authentication to "both" on my wireless router. Once I'd done that I got an IP address (still not sure if DNS settings got replicated as I'd hacked those earlier)

---

### Post by Fuzzypants on 2006-10-27
I changed /etc/network/interfaces, but it didn't help.  And dhcpcd didn't work any better for me, either.

I get this in /var/log/syslog while dhclient is looking for an address:

> 
Oct 26 21:39:59 localhost kernel: [17184582.324000] eth1: no IPv6 routers present


I also get this in /var/log/syslog when I run **sudo iwconfig eth1 essid Compound2**:

> 
Oct 26 21:45:03 localhost kernel: [17184898.448000] ndiswrapper (set_essid:61): setting essid failed (C00000BB)


---

### Post by wieman01 on 2006-10-27
The error message is no problem at this stage. IPV6 won't keep you from connecting... The performance may suffer a bit, but we'll see to that later.

_Questions:_
1. Have you installed Wifi-Radar & Gnome-Network-Manager?
2. Have you got Firestarter running or have configured IP tables?
3. "Compound2" says that the encryption is turned on. Is that your network? Please turn encryption/authentication off for the time being.

---

### Post by Fuzzypants on 2006-10-27
I turned encryption off, it didn't work.  I tried channels all over the band, but that didn't work, either.

I installed Wi-Fi Radar just now (I had never heard of it before), but it suffers from the same problems.  It will find the networks just find, but when I try to connect, it fails to aquire an IP address, with this error in /var/log/syslog:

> 
localhost kernel: [17181956.240000] (iw_get_essid:174): getting essid failed (C00000BB)


I haven't installed Gnome-Network-Manager (I couldn't find it in the repository, but I think I just found it, and I'll try that out next).

I'm not running Firestarter, and haven't touched the IP tables.  This is a brand new Ubuntu 6.01 installation, all I did was update, and follow the guide I linked to in my first post.

---

### Post by Fuzzypants on 2006-10-27
Ok, I got gnome-network-manager up and running.  It doesn't seem to have a problem with finding a network on the LAN (eth0), but it still can't find anything on the wireless.  It may be interesting to note that if I click on the icon in the toolbox, I don't see any options for wireless, just a single radio button labeled "Wired Network".

---

### Post by wieman01 on 2006-10-27
Can you please uninstall all wireless tools & do another scan?
> sudo apt-get remove network-manager knetworkmanager network-manager-gnome wifi-radar
> iwlist scan
Please post the results. Want to check again...

---

### Post by Fuzzypants on 2006-10-27
```

al@fuzzypants:~$ sudo apt-get remove network-manager knetworkmanager network-manager-gnome wifi-radar
Reading package lists... Done
Building dependency tree... Done
Package knetworkmanager is not installed, so not removed
The following packages will be REMOVED:
  network-manager network-manager-gnome wifi-radar
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 2343kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 72664 files and directories currently installed.)
Removing network-manager-gnome ...
Removing network-manager ...
Removing wifi-radar ...

```
```

al@fuzzypants:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0D:88:88:2F:6F
                    ESSID:"Compound2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-62 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:16:B6:09:2D:CA
                    ESSID:"SexMuffin77"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-41 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:17:31:FB:14:F1
                    ESSID:"Jarrett"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-91 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.


```

---

### Post by wieman01 on 2006-10-27
Is this your network?
> SexMuffin77
All the others have encryption turn on...

---

### Post by Fuzzypants on 2006-10-27
No, that is my neighbors.  Compound2 is my network.  I keep the encryption on unless I'm actively trying to connect to it, since there's more in this network than just my malfunctioning laptop.  And the channel is set to 11 because I was going through the band trying to find a channel that it might like to connect on.

Back to diagnostic mode:

```

          Cell 03 - Address: 00:0D:88:88:2F:6F
                    ESSID:"Compound2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

---

### Post by wieman01 on 2006-10-27
Alright... Then no surprise you cannot connect. Your "/etc/network/interfaces" will look a bit different in that case (assuming that you are using WEP, not WPA):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid [COLOR="Red"]Compound2[/COLOR]
wireless-key [COLOR="Red"]s:your_plain_text_key[/COLOR]
Please add your ASCII WEP key right after the little "s:". Then restart the wireless network (make sure the ethernet cable is unplugged):
> sudo ifdown eth1
> sudo ifup eth1
_**EDIT:**_
You can also add the HEX key should you prefer that:
> wireless-key [COLOR="Red"]your_hex_key[/COLOR]

---

### Post by wieman01 on 2006-10-27
If WEP is turned off, then skip "wireless-key"... Please also pay attention to the channel.

---

### Post by Fuzzypants on 2006-10-27
Thanks for putting up with me so long...  It seems like I have all my ducks in a row on this end, yet it just won't connect.  Marvel at my most recent failure:

```

al@fuzzypants:~$ sudo cat /etc/network/interfaces
Password:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Compound2
wireless-channel 6
al@fuzzypants:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:51:53:96
                    ESSID:"MOGnet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-93 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:16:B6:09:2D:CA
                    ESSID:"SexMuffin77"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-42 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0D:88:88:2F:6F
                    ESSID:"Compound2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-40 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

al@fuzzypants:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:42:37:45
Sending on   LPF/eth1/00:90:4b:42:37:45
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
al@fuzzypants:~$

```

---

### Post by Fuzzypants on 2006-10-27
More info:

```

al@fuzzypants:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:90:4B:42:37:45
          inet6 addr: fe80::290:4bff:fe42:3745/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d0002000-d0004000

al@fuzzypants:~$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:off/any  Nickname:"Compound2"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by wieman01 on 2006-10-27
Deleted...

---

### Post by wieman01 on 2006-10-27
Network definitely set to **DHCP**, right?

---

### Post by wieman01 on 2006-10-27
Hang on... But you are not connecting via Ethernet while you are trying to connect via wireless, are you? You cannot do both at the same time... as far as I know.

---

### Post by Fuzzypants on 2006-10-27
I just checked, and the network is definitely set to DHCP.  Windows computers (including this laptop, when it had Windows on it) can connect fine, too (to Compound2 or SexMuffin77), so I'm fairly sure there's nothing wrong with the network's configuration.

---

### Post by wieman01 on 2006-10-27
And no MAC filtering?

---

### Post by Fuzzypants on 2006-10-27
MAC filters are disabled.

---

### Post by wieman01 on 2006-10-27
And Ethernet is disconnected as well?

---

### Post by Fuzzypants on 2006-10-27
disconnected and disabled.

---

### Post by wieman01 on 2006-10-27
Ok, I think we need to chat via AIM... Need to go offline now, but we can continue tomorrow. You find my alias in my profile. Guess that's a bit more efficient if we chat tomorrow. We're close.

---

### Post by wieman01 on 2006-10-27
Last note: Have you tried disactivating & activating the card using Gnome's graphical networking applet?

---

### Post by wieman01 on 2006-10-27
I know it sounds odd but there is one last thing we can do today... Despite the fact that you are running DHCP, we can give your computer a static IP. I have seen this work in same cases. To do so update "/etc/network/interfaces":
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet **[COLOR="Red"]dhcp[/COLOR]**
wireless-essid [COLOR="Red"]Compound2[/COLOR]
[COLOR="Blue"]address 192.168.xxx.xxx
netmask 255.255.255.0
gateway 192.168.xxx.xxx
dns-nameservers 192.168.xxx.xxx[/COLOR]
"address" is your own address. Make sure the first 3 tokens are the same as your router's, you are free to make your own choice as far as the last bit is concerned (e.g. 100). "gateway" as well as "dns-nameservers" are your router's IP address.

Then restart the network.

_**EDIT:**_
**[COLOR="Red"]dhcp[/COLOR]** is no typo...

---

### Post by Fuzzypants on 2006-10-27
Is that System->Administration->Networking?  If so, then yes, otherwise, I'm not sure which tool you're talking about.

---

### Post by wieman01 on 2006-10-27
> **Fuzzypants said:**
> Is that System->Administration->Networking?  If so, then yes, otherwise, I'm not sure which tool you're talking about.
Yes, that's the one. See you tomorrow.

---

### Post by Fuzzypants on 2006-10-27
Should that be "iface eth1 inet static"?  I tried it both ways, and still no luck.

---

### Post by wieman01 on 2006-10-27
You can try both, but the odd thing is that "iface eth1 inet dhcp" works nonetheless. Done it myself once...

---

### Post by wieman01 on 2006-10-27
What happens you try connecting to your neighbor's network:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid [COLOR="Red"]SexMuffin77[/COLOR]
[COLOR="Blue"]wireless-channel 6[/COLOR]
Then restart the network:
> sudo /etc/init.d/networking restart
Now I am running out of ideas at this point. I have no clue why the wireless adapter can scan fine but won't connect. All I can offer is that you compare Ubuntu's network settings with those in Windows. I suggest that we chat over AIM any time soon.

There is a howto which should be our last resort (if everything fails). It makes use of "ndiswapper", however. But it's worth a read: [http://www.ubuntuforums.org/showthread.php?t=25683]("http://www.ubuntuforums.org/showthread.php?t=25683")

---

### Post by Starlight on 2006-10-29
Hi! I have the same, or very similar problem.... maybe it's because your card is 802.11g and access point it 802.11b? The same is with my card, but I don't know how to change it to 802.11b to see if it can fix that....

---

### Post by wieman01 on 2006-10-29
> **Starlight said:**
> Hi! I have the same, or very similar problem.... maybe it's because your card is 802.11g and access point it 802.11b? The same is with my card, but I don't know how to change it to 802.11b to see if it can fix that....
That is possible if the router is a G-router and does not have B enabled, and the wireless adapter is B. But a wireless G adapter should be able to connect to a wireless B router with no problem. 

But perhaps it's worth a try...

---

### Post by wieman01 on 2006-10-29
Hello Fuzzypants, 

Found you card on the list of adpater supported by "ndiswrapper". Since the Broadcom chipset gives us a headache, would you want to try "ndiswrapper" instead?

List of devices: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

Guide ("ndiswrapper"): [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by Starlight on 2006-10-29
I've just checked, and changing from G to B didn't fix anything... I still can't connect to any access point, even though I can see them...

---

### Post by wieman01 on 2006-10-29
> **Starlight said:**
> I've just checked, and changing from G to B didn't fix anything... I still can't connect to any access point, even though I can see them...
So now there are 2 people with the same problem and other users reporting that Broadcom adapters are somewhat troublesome. If that does not call for... (DRUM)... "ndiswrapper"... the dreaded word!

Guys, 

Just came across this guide... It looks excellent: [http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

---

### Post by Starlight on 2006-10-29
actually, I'm using ndiswrapper.... the Linux driver for my RT61 card compiles with some weird warnings, and even though it compiles the module, I get the "invalid module format" error when trying to use it.

---

### Post by wieman01 on 2006-10-29
But you are not using "ndiswrapper" and the Linux driver at the same time, are you?

---

### Post by Starlight on 2006-10-29
no, i disabled it... it doesn't work anyway

---

