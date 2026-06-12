---
title: "start network on boot"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by jgw on 2014-11-21
I am running with 12.10  I have a wired network connection  My network does not start at boot.  I am also using PIA for a vpn which runs automatically when the network starts.  After the machine boots I click on the little windshield icon, then click on "wired connection 2" and the network/vpn take right off.  I have searched for a solution and there seems to be a lot of those.  My thought is that this is probably a really easy fix so I thought I would ask how to make the network run at boot.  I should also add that I have another linux machine that automatically runs the network at boot so I suspect I knew the answer once (mind failing a bit I fear)

I did install and run BUM, check to startup the network at boot - didn't work.

Thank you...........

---

### Post by houstonbofh on 2014-11-21
What is the contents of /etc/network/interfaces

---

### Post by jgw on 2014-11-21
Thanks for the reply.

Contents of /etc/network/interfaces:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

---

### Post by jgw on 2014-12-18
I am now booting up with my network.  What I did was to remove the checkmark, in networks, to start my vpn when I startup.  I will mark this as done.

---

### Post by Bucky Ball on 2014-12-18
Off-topic, but you might want to consider upgrading to a supported release. You would be getting no updates/upgrades for 12.10, and that includes security updates, so effectively your security updates are over a year out of date. This can create security vulnerabilities if the machine is online. Your chances of support when things go wrong will dwindle as time goes on and things will possibly deteriorate so you could find yourself backed into a corner and having to upgrade, anyway. 

Good luck. ;)

---

