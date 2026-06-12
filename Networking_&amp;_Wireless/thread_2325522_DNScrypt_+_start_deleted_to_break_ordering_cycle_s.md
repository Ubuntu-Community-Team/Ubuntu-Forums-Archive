---
title: "DNScrypt + start deleted to break ordering cycle starting with sockets.target/start"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by cokeflash82 on 2016-05-23
Hi!

At boot.log:

SKIP [0m] Ordering cycle found, skipping dnscrypt-proxy listening socket


I get this error @ DNScrypt:

intel@666:~$ systemctl status dnscrypt-proxy.socket -l
&#9679; dnscrypt-proxy.socket - dnscrypt-proxy listening socket
   Loaded: loaded (/etc/systemd/system/dnscrypt-proxy.socket; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/dnscrypt-proxy.socket.d
           &#9492;&#9472;override.conf
   Active: inactive (dead)
   Listen: 127.0.0.1:53 (Stream)
           127.0.0.1:53 (Datagram)


Mai 23 14:03:18 666 systemd[1]: dnscrypt-proxy.socket: Job dnscrypt-proxy.socket/start deleted to break ordering cycle starting with sockets.target/start

/etc/systemd/system/dnscrypt-proxy.socket.d/override.conf
[Socket]
ListenStream=
ListenDatagram=
ListenStream=127.0.0.1:53
ListenDatagram=127.0.0.1:53

[B]Can someone help please?
[/B]

---

