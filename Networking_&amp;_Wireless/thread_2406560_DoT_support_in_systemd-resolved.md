---
title: "DoT support in systemd-resolved"
date: 2018-11-22
forum: Networking &amp; Wireless
---

### Post by fgont on 2018-11-22
Folks,
I'm running a fresh install of 18.10. I configured as:
[Resolve]
DNS=1.1.1.1
#FallbackDNS=
Domains=~.
#LLMNR=no
#MulticastDNS=no
#DNSSEC=no
DNSOverTLS=opportunistic
#Cache=yes
#DNSStubListener=yes
Still, when running tcpdump it seems systemd-resolved still tries to use (in parallel with 1.1.1.1) the DNS advertised by the DHCP server.
My assumption was that setting:
Domains=~.
would prevent that.
Any clues?
Thanks!
Fernando

---

### Post by logix2 on 2018-11-22
Try setting the DNS in the Network settings. Something like in [this]("https://1.bp.blogspot.com/-UvSMOTZV3lw/W9giY-uH-jI/AAAAAAAABwc/kGdp7659DksNS-TAqNfW7DS0zYEk0XilgCLcBGAs/s1600/network-dns-gnome-ubuntu1810.png") screenshot, but using 1.1.1.1 as the DNS (the DNS in the screenshot is for DNSCrypt Proxy 2).

---

### Post by fgont on 2018-11-24
Did you read my post?

---

### Post by philhughes on 2018-11-29
You don't say if you are on desktop or server. If desktop, the following may help. If you look at this guide for setting up Stubby [1], it says to explicitly set the DNS entry in NetworkManager (in the case of Stubby, the default is 127.0.0.1). It may be worth trying 127.0.0.53 here, even though this is already set in /etc/resolv.conf.

The DoT support in systemd-resolved seems a bit half-baked at the moment. There is no certificate checking for the DNS server [2] so it is subject to MITM attacks, and there is no support for strict mode [3], so it is subject to downgrade attacks.

Let us know how you get on.

[1] [https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls](https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls)
[2] [https://github.com/systemd/systemd/issues/9397](https://github.com/systemd/systemd/issues/9397)
[3] [https://github.com/systemd/systemd/issues/10755](https://github.com/systemd/systemd/issues/10755)

---

