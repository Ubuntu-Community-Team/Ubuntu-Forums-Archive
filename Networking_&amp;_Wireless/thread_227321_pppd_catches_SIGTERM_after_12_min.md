---
title: "pppd catches SIGTERM after 1/2 min"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by /dev/urandom on 2006-08-01
Hi,
my PC is connected via DSL-Modem and starts a working connection on boot.
( If I'm fast enough I can login on F1 and ping to hosts on the internet. Doing so the connection gets interrupted after 1/2 minute: unknown host )
ifconfig shows interface ppp0 still running.
I can start a ppp1 doing:

$ sudo pon dsl-provider

or first killing ppp0 with

$ sudo poff
$ sudo pon dsl-provider

both work fine creating a stable connection.

# egrep -v "^#|^$" /etc/network/interfaces
auto lo
iface lo inet loopback
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf


# less /var/log/messages
...
Aug  1 14:19:30 christiana-desktop kernel: [17179605.184000] Bluetooth: RFCOMM ver 1.7
Aug  1 14:19:36 christiana-desktop pppd[3394]: PPP session is 2786
Aug  1 14:19:36 christiana-desktop kernel: [17179611.176000] NET: Registered protocol family 24
Aug  1 14:19:36 christiana-desktop pppd[3394]: Using interface ppp0
Aug  1 14:19:36 christiana-desktop pppd[3394]: Connect: ppp0 <--> eth0
Aug  1 14:19:41 christiana-desktop pppd[3394]: CHAP authentication succeeded
Aug  1 14:19:41 christiana-desktop pppd[3394]: CHAP authentication succeeded
Aug  1 14:19:41 christiana-desktop pppd[3394]: peer from calling number 00:90:1A:41:65:68 authorized
Aug  1 14:19:41 christiana-desktop pppd[3394]: local  IP address 85.178.17.247
Aug  1 14:19:41 christiana-desktop pppd[3394]: remote IP address 213.191.89.1
Aug  1 14:19:41 christiana-desktop pppd[3394]: primary   DNS address 213.191.74.18
Aug  1 14:19:41 christiana-desktop pppd[3394]: secondary DNS address 213.191.92.86
Aug  1 14:19:43 christiana-desktop kernel: [17179617.804000] ip_tables: (C) 2000-2002 Netfilter core team
Aug  1 14:23:36 christiana-desktop pppd[3394]: Terminating on signal 15
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Aug  1 14:23:36 christiana-desktop pppd[3394]: Connect time 4.0 minutes.
Aug  1 14:23:36 christiana-desktop pppd[3394]: Sent 800 bytes, received 2972 bytes.
Aug  1 14:23:36 christiana-desktop pppd[3394]: Connection terminated.
Aug  1 14:23:36 christiana-desktop pppd[3394]: Exit.
Aug  1 14:24:00 christiana-desktop pppd[4746]: Plugin rp-pppoe.so loaded.
Aug  1 14:24:00 christiana-desktop pppd[4748]: pppd 2.4.4b1 started by root, uid 0
Aug  1 14:24:00 christiana-desktop pppd[4748]: PPP session is 2932
Aug  1 14:24:00 christiana-desktop pppd[4748]: Using interface ppp0
Aug  1 14:24:00 christiana-desktop pppd[4748]: Connect: ppp0 <--> eth0
Aug  1 14:24:05 christiana-desktop pppd[4748]: CHAP authentication succeeded
Aug  1 14:24:05 christiana-desktop pppd[4748]: CHAP authentication succeeded
Aug  1 14:24:05 christiana-desktop pppd[4748]: peer from calling number 00:90:1A:41:65:68 authorized
Aug  1 14:24:05 christiana-desktop pppd[4748]: local  IP address 85.178.20.35
Aug  1 14:24:05 christiana-desktop pppd[4748]: remote IP address 213.191.89.1
Aug  1 14:24:05 christiana-desktop pppd[4748]: primary   DNS address 213.191.74.18
Aug  1 14:24:05 christiana-desktop pppd[4748]: secondary DNS address 213.191.92.86
Aug  1 14:25:14 christiana-desktop gconfd (christiana-4916): (Version 2.14.0) wird gestartet, Prozesskennung 4916, Benutzer »christiana«


No idea where the SIGTERM comes from.
Any hints appreceated.

regards
raina

---

