---
title: "[SOLVED] Atheros Wireless card Ibex, not working."
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Kavity on 2008-11-01
Hey,

I know there's been posts about wireless not working with Ibex, and I've read through them and followed some of the things posted, but I'm still running into problems.
My card is Atheros AR2413, and here's the lspci information
```
[kavity@Shadow:~$] lspci | grep Atheros
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```

It is ath0. I have configured my /etc/network/interfaces properly for it.
```
auto ath0
iface ath0 inet dhcp
address 192.168.2.14
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key ************************
wireless-essid BananaBoat

```
The "wireless-key" is set correctly in the actual file. It's 128-bit WEP.

When I run `ifup ath0` I get this:
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7e:02:17:4b
Sending on   LPF/ath0/00:19:7e:02:17:4b
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.14 from 192.168.2.1
DHCPREQUEST of 192.168.2.14 on ath0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.14 from 192.168.2.1
bound to 192.168.2.14 -- renewal in 129445 seconds.
 * if-up.d/mountnfs[ath0]: waiting for interface lo before doing NFS mounts

```

This all works fine, and I get connected, and can use the internet perfectly fine, but after about 5 minutes(maybe less), it stops working, and I have to `ifdown ath0`, and `ifup ath0` again if I want to use the connection, but again, it disconnects.

Anyone have any ideas what could be causing the problem?

---

### Post by Kavity on 2008-11-01
After doing all that, and the majority of other things posted on this site, it still wasn't working. So what I had to do was install the linux-backports-modules-intrepid, reboot, and all worked.

To get the modules run:

```
sudo apt-get install linux-backports-modules-intrepid
```

I had everything else set up for the wireless connection, so when I rebooted, I was greeted with a windows saying "You need to put in your WEP password." I put in the code, and now everything is working fine.

If anyone needs any more help on this, I can try and help, because I know how frustrating it can be waiting and hoping someone will come onto the forums and read your message/reply.

You can get me on msn at [email]Stuck_In_Eternity@hotmail.com[/email]

Good luck.

---

