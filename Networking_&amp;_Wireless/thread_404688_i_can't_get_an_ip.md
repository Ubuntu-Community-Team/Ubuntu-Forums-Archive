---
title: "i can't get an ip"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by RoMo on 2007-04-08
hello guys!

i have this problem on dapper:

i just got this new modem/router 2wire and i just can't get an ip adress with my laptop on ubuntu while on windows is very easy.

this thing turns its wireless light when a device conects to it, but i just cant make it work!

when i use wifi-radar it sees it, but i can't get an ip adress...

iwconfig:

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"INFINITUM2128"
          Mode:Managed  Channel=0  Access Point: 00:19:E4:97:47:99
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```


ifconfig:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2A:92:E7:27
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fe92:e727/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:919843 (898.2 KiB)  TX bytes:205993 (201.1 KiB)
          Interrupt:177 Base address:0xd400

eth1      Link encap:Ethernet  HWaddr 00:15:00:28:4B:E9
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x6000 Memory:febff000-febfffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

```

i have a intel pro 2200 bg wireless card, btw

i tried with dhclient and no luck =S

any help will be awesome!

---

### Post by rolando on 2007-04-08
Found this, any good?

[http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)

:)

---

### Post by teaker1s on 2007-04-08
I recommend 
```
network-manager-gnome
``` for ubuntu desktops most times it cures config issues

---

### Post by RoMo on 2007-04-08
> Found this, any good?

[http://www.debuntu.org/2006/03/27/9-...-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-...-debian-ubuntu)

hi! thanx a lot for the answer

unfortunately that didn't work for me :(  since my card **does** work with ubuntu, my card knows that all the wifi nets are there but i can't get an ip adress from it D=.

> 
 	I recommend
Code:

network-manager-gnome

for ubuntu desktops most times it cures config issues

no luck with network-manager either =S

i will keep trying!


edit: when i try to connect with wifi-radar it gives me 127.0.0.1 as ip =S

---

### Post by josephus on 2007-04-09
can you see the access point using
```
iwlist eth1 scan
```

---

