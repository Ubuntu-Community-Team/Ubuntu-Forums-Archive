---
title: "wireless, the harbringer of doom"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2006-09-09
I have installed Xubuntu, and of course the wireless is the ONLY thing that screws up. Pretty amazing, considering that I have had all sorts of issues before!

Anyways. this is a similar problem to one I had with Ubuntu when I installed that on my laptop, but for some reason it worked after a random number of attempts. This isn't. I try using the Network Settings thing, but that never seems to be able to connect to the network. 

I can't ping, so it isn't the DNS.

Output from iwconfig:
```
lo
      no wireless extensions. [?!?]

eth0
      IEEE 802.11b/g ESSID:"home" Nickname:"Broadcom 4306"
      Mode:Managed Access Point: Invalid  Bit Rate=1 Mb/s
      RTS thr:off   Fragment thr:off
      Link Quality:0  Signal level:0  Noise level:0
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
      Tx excessive retries:0 Invalid misc:0  Missed beacon:0

sit0
      no wireless extentions
```

The ping just says "connect: Network is unreachable"

I have connected before with MEPIS, which is loosely based on Dapper, though it did take a couple (hundred) forum posts...

Is there any way I can connect without having to use the little box - terminal, perhaps? If anyone has an idea, plase do give it in np0b terms :D

Thanks, 
K

---

### Post by linuxusr50 on 2006-09-09
Your wireless card "eth0" is not gettng an IP.

Make sure you have DHCP enabled in your router and make sure you have IP's in the pool.

Run the following:

```
sudo ifup --all
```
```
sudo dhclient
```

Then show the results of ifconfig again.

---

### Post by Kulgan on 2006-09-09
ok... let's see... I have a feeling that that did not work quite as it is supposed to. You, however, may be able to discern the output and figure out some intelligent course of action...

ifup --all:
```
kulgan@ubuntu:~$ sudo ifup --all
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

odd that it started with eth1, rather than eth0...

dhclient:
```
kulgan@ubuntu:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth0/00:11:50:08:88:d0
Sending on   LPF/eth0/00:11:50:08:88:d0
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

At least it is doing it on the right device this time... 

Did you mean ifconfig or iwconfig? Well, did them both...
ifconfig:
```
kulgan@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1356 (1.3 KiB)  TX bytes:1356 (1.3 KiB)
```

iwconfig:
```
kulgan@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I see in here "Rx invalid crypt:0" I do have a hex WEP key...

thanks,
Kulgan

---

### Post by linuxusr50 on 2006-09-10
I have included my tests after running the same commands.  I would like to  see the contents of your /etc/networks/interfaces file.  This may give some insite.



OUTPUT AFTER RUNNING sudo dhclient

```
$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:12:79:5a:91:f9
Sending on   LPF/eth0/00:12:79:5a:91:f9
Listening on LPF/eth1/00:06:25:18:8b:dc
Sending on   LPF/eth1/00:06:25:18:8b:dc
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.8.26.254
bound to 10.8.26.100 -- renewal in 17316 seconds.

```


OUTPUT AFTER RUNNING iwconfig

```
eth1      IEEE 802.11b  ESSID:"myessid"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:37:A9:0C
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=5/153  Noise level=112/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


OUTPUT AFTER RUNNING sudo dhclient

```
eth1      Link encap:Ethernet  HWaddr 00:06:25:18:8B:DC
          inet addr:10.8.26.100  Bcast:10.8.26.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fe18:8bdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:109963 (107.3 KiB)  TX bytes:71134 (69.4 KiB)
          Interrupt:3 Base address:0x4100

```

---

### Post by Kulgan on 2006-09-11
> I would like to see the contents of your /etc/networks/interfaces

make that /etc/network/interfaces :P

content:
```
auto lo
iface lo inte loopback

auto eth 0
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

thanks,
K

--
tried adding 
"wireless essid <essid>
wireless-key <key>"

to it...
no results. I guess I have to refrefsh the connetion for this to have any effect? If so, how would I do such a thing?

thanks again
--

---

### Post by bensexson on 2006-09-11
Look here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by linuxusr50 on 2006-09-11
**Kulgan:**

To refresh your connections just run:

```
sudo ifdown eth0
```
```
sudo ifup eth0
```

---

### Post by linuxusr50 on 2006-09-11
**Kulgan:**

Just noticed something that problably has no bearing but you may want to correct it and try again.

In your interfaces file you have included a space between "eth" and "0".  I am not sure if the space would have an effect but it would probably be wise to correct it anyway.
> 
auto eth 0
iface eth0 inet dhcp

---

### Post by Kulgan on 2006-09-14
I believe that that was a typo on my side - I was just typing it on a different machine...

Unfortuneately, I can't check, as there is something wrong with the whole thing now, for any O/S. Fine untill I select an O/S, then the screen stops showing stuff. But that's not really "networking" related, so I'll have a look somewhere else. I might just get a whole new machine and test what went wrong. Not the screen or gpx card. anyways... Thanks for the link, btw, bensexson, it looks like what I need to do for yet another machine... lol

K

---

