---
title: "[SOLVED] Network restart is needed when router is unplugged"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by bruno321 on 2008-08-15
Hi. Using the search option I've found several people have the same problem I do, which is the following: wireless network won't start unless I do 'sudo /etc/init.d/networking restart' . Which I can live with. I've managed long ago to create a script which does that every time the machine boots up. It works, it doesn't bother me, but it's not a real fix.

So the problem persists in this fashion: whenever the router is disconnected (so I lose my wireless connection), it won't reconnect, and I have to do it manually. This is a real, real pain, because it happens often (nevermind why), and because it kills any ongoing transfer I was doing. So if for example I was away, and the router gets disconnected and inmediately reconnected, then the network connection won't reconnect, so if I was downloading a file it will have stopped downloading, even if the router was connected.

I'm using Kubuntu 7.10, here's my interfaces file:

auto wlan0
iface wlan0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.253
wireless-essid BLAHBLAH
wireless-key BLAHBLAH

and my iwconfig:

```
wlan0     IEEE 802.11g  ESSID:"BLAHBLAH"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:09:75:E2
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Signal level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by bruno321 on 2008-08-23
Okay, this has been solved. See [here]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/network-restart-is-needed-when-router-is-unplugged-663021/#post3257112").

---

