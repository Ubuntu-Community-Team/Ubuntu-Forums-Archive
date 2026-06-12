---
title: "Wireless DHCP problems on 7.04/feisty fawn (solved)"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by pollyp on 2007-11-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/105872](https://bugs.launchpad.net/ubuntu/+bug/105872) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi everyone,

I had a problem with DHCP over a wireless connection on Ubuntu 7.04/Feisty Fawn that I've resolved. I wanted to post the solution here, in case anyone else runs into the same issue.

My problem was that I couldn't get an IPv4 address via DHCP over my wireless interface. However, DHCP worked fine over my wired interface, and if I configured my wireless interface to use a static address that worked too. Because roaming mode assumes that it's a DHCP client, that didn't work either.

Iwconfig reported sensible values in both the DHCP and static cases. However, ifconfig would sometimes report a eth1:avah interface in addition to my wireless eth1 interface. The eth1:avah interface was transient, so you have to run ifconfig repeatedly to see this.

I came across this bug report which seemed to be related: [https://bugs.launchpad.net/ubuntu/+bug/105872](https://bugs.launchpad.net/ubuntu/+bug/105872). Per poster pooryorick's suggestion,  I removed /etc/network/*/avahi* and that fixed the problem.

This was on a i386 machine, using the alternate CD install. I'm using an Orinoco 802.11B "silver" card, and the orinoco_cs driver.

-Polly

---

### Post by spd106 on 2007-11-22
I don't believe that avahi was the main cause of your problem, but it is certainly the most obvious symptom. Usually this sort of thing comes about from Network Manager timing out too quickly, however the devs have said many times that it's not something they will fix. So instead you have to disable avahi.

On a related note, it might be worth just deleting the avahi-autoip scripts and not avahi-daemon as that shouldn't affect DHCP at all.  Removing avahi-daemon will prevent some features that rely on it from working properly e.g. Rhythmbox DAAP music sharing.

---

### Post by pollyp on 2007-11-29
Thanks for the informative followup. I'm curious about why the Network Manager developers are reluctant to tackle this. Can you point me to a relevant thread or bug report?

---

