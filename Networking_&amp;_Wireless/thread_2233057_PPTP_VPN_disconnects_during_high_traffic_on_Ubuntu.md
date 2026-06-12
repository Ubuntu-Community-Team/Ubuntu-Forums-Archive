---
title: "PPTP VPN disconnects during high traffic on Ubuntu 14.04"
date: 2014-07-06
forum: Networking &amp; Wireless
---

### Post by gordon6 on 2014-07-06
I've been trying for days to get my office VPN to stay working in Ubuntu 14.04. It's a PPTP VPN, with MSCHAPv2 authentication and 128-bit MPPE encryption.

What happens is the VPN connects fine and I can access all my office resources and the internet. However, as soon as I do anything at all bandwidth-intensive, the VPN drops almost instantly. It doesn't disconnect, but there is simply no traffic. Connecting to any site (by Domain or IP) just causes it to hang and timeout. In my case, I'm trying to check out a subversion repository, and every time I start the checkout, the connection dies within 30 seconds.

I've tried basically every combination of the advanced settings I can think of. I've turned PPP echo on and off, turned off all the compression. I've turned off automatic route configuration and manually set my VPN routes (as well as DNS servers.) I've tried completely disabling IPv6 for Ubuntu (my VPN does not support IPv6, not that this should make any difference.) Nothing makes any difference at all.

syslog does not report any errors at all when the connection drops (well, after a few minutes I get a "whoopsie: offline" error, which I assume is just the OS realizing it has no internet access.)

I've read probably 20 VPN threads on these forums but have not found anything useful for my situation. I also installed Ubuntu on a completely different system and set up the VPN from scratch – the result was the same.

The VPN works perfectly in OS X and Windows.


My current configuration:
[IMG]https://dl.dropboxusercontent.com/u/10577704/ubuntu_vpn.png[/IMG]

---

### Post by ris2t on 2015-03-06
Hi 

Did you find any solution to this? Been experience similar issues on Ubuntu 14.10. PPTP VPN comes up, runs ok for a couple of minutes or until any load (e.g. bittorrent) is run through it. Once loaded it quickly stops responding.

Logs generally show the following. Once that appears the VPN doesn't work, still up through.
No ping, no dns resolution, just the LCP ProtRej errors.

> 
Mar  6 23:12:42 Hammerstien pppd[10875]: rcvd [proto=0xcb] 5e 05 1d fd 53 76 f7 c9 d1 e4 76 47 d0 3c 18 36 6f 0a a2 6d 23 b8 39 ad f4 07 ff bb 17 f6 78 8f ...
Mar  6 23:12:42 Hammerstien pppd[10875]: Unsupported protocol 0xcb received
Mar  6 23:12:42 Hammerstien pppd[10875]: sent [LCP ProtRej id=0x4 00 cb 5e 05 1d fd 53 76 f7 c9 d1 e4 76 47 d0 3c 18 36 6f 0a a2 6d 23 b8 39 ad f4 07 ff bb 17 f6 ...]

Tried all the google suggestion with no success. 
Tested a clean 14.10 booted from USB in trail mode and same issue experieced.

SwitchVPN service is the target
mppe 128bit, mschapv2
MTU - set down to 1200, no impact
various compressions on and off, and echos - no impact

Curiously my Window laptop running PPTP seems to run and stay up, suggesting a linux library type issue.

---

### Post by gordon6 on 2015-03-06
> **ris2t said:**
> Hi 

Did you find any solution to this? Been experience similar issues on Ubuntu 14.10. PPTP VPN comes up, runs ok for a couple of minutes or until any load (e.g. bittorrent) is run through it. Once loaded it quickly stops responding.

Logs generally show the following. Once that appears the VPN doesn't work, still up through.
No ping, no dns resolution, just the LCP ProtRej errors.



Tried all the google suggestion with no success. 
Tested a clean 14.10 booted from USB in trail mode and same issue experieced.

SwitchVPN service is the target
mppe 128bit, mschapv2
MTU - set down to 1200, no impact
various compressions on and off, and echos - no impact

Curiously my Window laptop running PPTP seems to run and stay up, suggesting a linux library type issue.

Nope. Spent forever on it, gave up and just run it in a VM on an OS X system and share the host's VPN connection when I need to use Linux.

---

### Post by CrusaderAD on 2015-10-05
Bump, any updates?

---

### Post by Robert_Jacques on 2015-12-30
I'm experiencing the same issue, do i need to move the VPN client upstream?

---

