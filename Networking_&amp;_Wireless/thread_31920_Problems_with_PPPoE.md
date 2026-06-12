---
title: "Problems with PPPoE"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by Rhawi Dantas on 2005-05-05
I have a brand new Ubuntu installation and configured my internet connection with pppoeconf but I have a problem that is a little bit hard to spot...

When I connect to the internet is everything normal, but after some time I can't browse anymore... I just stay connected to GAIM and then after some time it drops down also...

I have an ADSL connection with 3Com HomeConnect and VIA Rhine/DragonFly...

/etc/ppp/peers/dsl-provider
```

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
mtu 1412
usepeerdns
plugin rp-pppoe.so eth0

```

When the connection is broken
/var/log/messages
```

 6 09:46:22 localhost kernel: IPv6 over IPv4 tunneling driver
May  6 09:46:22 localhost pppd[6306]: pppd 2.4.2 started by root, uid 0
May  6 09:46:22 localhost pppd[6306]: PPP session is 47405
May  6 09:46:22 localhost pppd[6306]: Using interface ppp0
May  6 09:46:22 localhost pppd[6306]: Connect: ppp0 <--> eth0
May  6 09:46:22 localhost pppd[6306]: Couldn't increase MTU to 1500
May  6 09:46:22 localhost pppd[6306]: Couldn't increase MRU to 1500
May  6 09:46:22 localhost pppd[6306]: Couldn't increase MRU to 1500
May  6 09:46:22 localhost pppd[6306]: PAP authentication succeeded
May  6 09:46:22 localhost pppd[6306]: peer from calling number 00:30:85:95:52:43 authorized
May  6 09:46:22 localhost pppd[6306]: local  IP address 201.9.131.218
May  6 09:46:22 localhost pppd[6306]: remote IP address 200.164.195.25
May  6 09:46:22 localhost pppd[6306]: primary   DNS address 200.165.132.155
May  6 09:46:22 localhost pppd[6306]: secondary DNS address 200.149.55.142
----------------------------
May  6 01:14:55 localhost pppd[11352]: Plugin rp-pppoe.so loaded.
May  6 01:14:55 localhost pppd[11352]: RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
May  6 01:14:55 localhost pppd[11355]: pppd 2.4.2 started by root, uid 0
May  6 01:14:55 localhost kernel: eth0: link up, 10Mbps, half-duplex, lpa 0x0021
May  6 01:15:03 localhost pppd[11355]: PPP session is 45442
May  6 01:15:03 localhost pppd[11355]: Using interface ppp0
May  6 01:15:03 localhost pppd[11355]: Connect: ppp0 <--> eth0
May  6 01:15:03 localhost pppd[11355]: Couldn't increase MTU to 1500
May  6 01:15:03 localhost pppd[11355]: Couldn't increase MRU to 1500
May  6 01:15:03 localhost pppd[11355]: Couldn't increase MRU to 1500
May  6 01:15:03 localhost pppd[11355]: PAP authentication succeeded
May  6 01:15:03 localhost pppd[11355]: peer from calling number 00:30:85:95:52:43 authorized
May  6 01:15:03 localhost pppd[11355]: local  IP address 201.9.131.247
May  6 01:15:03 localhost pppd[11355]: remote IP address 200.164.195.25
May  6 01:15:03 localhost pppd[11355]: primary   DNS address 200.165.132.155
May  6 01:15:03 localhost pppd[11355]: secondary DNS address 200.149.55.142
May  6 01:18:01 localhost kernel: NTFS driver 2.1.22 [Flags: R/O MODULE].
May  6 01:18:01 localhost kernel: NTFS volume version 3.1.
May  6 01:46:23 localhost -- MARK --
May  6 01:51:54 localhost pppd[11355]: Terminating on signal 15.
May  6 01:51:54 localhost pppd[11355]: Connect time 36.9 minutes.
May  6 01:51:54 localhost pppd[11355]: Sent 1051008 bytes, received 5445839 bytes.
May  6 01:51:54 localhost pppd[11355]: Couldn't increase MTU to 1500
May  6 01:51:54 localhost pppd[11355]: Couldn't increase MRU to 1500
May  6 01:51:54 localhost pppd[11355]: Connection terminated.
May  6 01:51:54 localhost pppd[11355]: Exit.

```

/etc/resolv.conf
```

nameserver 200.165.132.155
nameserver 200.149.55.142
search dummy.net

```

Well... thats pretty much what's going on...
Thanks for the help

---

### Post by wildtiger23 on 2005-05-05
Have you tried to change the mtu setting for 1492....?

---

### Post by alastair on 2005-05-05
You also have "persist" in the options file - does it re-dial?

Some ISP's have an "inactivity" timeout perhaps i.e. drop the connection if no data passes after some time?

---

