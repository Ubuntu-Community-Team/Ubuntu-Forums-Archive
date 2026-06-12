---
title: "Eth0 goes down on a Vaio"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by Ufic on 2006-12-15
Hi.

I installed Kubuntu Edgy on a Sony Vaio VGN-N11M and now I'm having a problem.

When I download large packages (for example if I run sudo apt-get update or if I try to download a file larger than 500k), eth0 go down and I have to set it up and rerun sudo dhclient).

Any help is appreciated...
Thanks in advance

Some useful informations:
[LIST]
[*] I use a Fastweb fiber optics connection by an hub.
[*] Using Windows on Vaio or Kubuntu on another PC it works.
[*] When I set eth0 up, dmesg says sky2 eth0: Link is up at 10 Mbps, half duplex, flow control none.
[*] When it don't works, dhclient (after failing) says No working leases in persistent database - sleeping
[/LIST]

---

