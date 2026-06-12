---
title: "get ntp-servers from DHCP with networkmanager?"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by abrahamsmith on 2007-09-09
I am running Xubuntu Feisty, and I am also using network-manager to control my networking.

network manager (hence dhcdbd (hence dhclient)) does not seem to read ntp-servers suggested by the DHCP server.  The expected behavior is that  something in that chain of programs to update /etc/ntp.conf.  How does one enable this?

I tried adding ntp-servers to the "request" line in /etc/dhcp3/dhclient.conf, but that seemed to have no effect.

(If it matters, I am just using ntpdate so far, though this problem *should* be independent of the ntp client I am using.)

---

### Post by abrahamsmith on 2007-09-09
NEVERMIND.    I'm an idiot.

My DHCP server was misconfigured.  ntp updates with dhclient and network-manager act more-or-less as expected.

---

