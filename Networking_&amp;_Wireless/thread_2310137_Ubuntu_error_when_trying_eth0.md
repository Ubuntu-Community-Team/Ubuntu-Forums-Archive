---
title: "Ubuntu error when trying eth0"
date: 2016-01-16
forum: Networking &amp; Wireless
---

### Post by wheezy2 on 2016-01-16
I have two virtual machines running, Damn Small Linux, which is acting as a firewall, and Ubuntu, both running on VirtualBox.
Damn Small Linux's Adapter 1 is attached to NAT and Adapter 2 is attached to an Internal Network. On Damn Small Linux I ran ifconfig eth1 10.0.3.1 and it executed fine.
On Ubuntu I have Adapter 1 just as an Internal Network since it's supposed to connect through the firewall because I'm trying to create a TOR Only Environment on the Ubuntu machine.
Whenever I run
[I]sudo bash
ifconfig eth0 10.0.3.2[/I]
it returns 
[I]SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device

[/I]--------------------------------
Here is what ifconfig -a looks like
[IMG]https://i.gyazo.com/9810ff9c7d6b4f9901168fb452d5c636.png[/IMG]

---

### Post by Frogs Hair on 2016-01-16
Moved to ***Networking & Wireless***

---

### Post by grahammechanical on 2016-01-16
Have you tried running that command with enp0s3 instead of eth0?

Why terms like eth0 & eth1 are no longer being used, I have no idea. Or wlan0 for that matter. The little research I have done points to systemd spreading its tentacles.   Those  strange labels seem common on Redhat and those distros based on Redhat.

regards

---

