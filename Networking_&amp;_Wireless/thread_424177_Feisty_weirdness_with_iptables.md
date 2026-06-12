---
title: "Feisty weirdness with iptables"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by mdoube on 2007-04-26
Hi All,

We've had a bit of web browsing weirdness in the lab on a number of new distros, including Ubuntu Feisty, Fedora core 6, Mandriva etc. We could connect to the 'Net and do most things except browse most websites. The exceptions were Google (including gmail), bbc.co.uk, and the qmul.ac.uk intranet. Everything else failed - an http connection was made but would time out while waiting for data. We could traceroute, ping and everything. Ubuntu Dapper and Edgy were not affected. Presumably there has been a change in the kernel.

Turns out there is a problem with our gateway, so this option had to be set in iptables:

```
iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
```

You can read about the problem here:

```
man iptables
```

The quickest solution for us was to download and install [firestarter]("https://bugs.launchpad.net/ubuntu/+source/firestarter/1.0.3-2ubuntu1") . You could also get firestarter from the Universe repo. 3 button-clicks and everything worked!

If anyone has a better solution please let us know.

Cheers,

Mike

---

