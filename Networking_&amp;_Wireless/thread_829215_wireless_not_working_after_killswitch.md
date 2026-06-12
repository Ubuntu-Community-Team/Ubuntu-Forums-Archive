---
title: "wireless not working after killswitch"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by Arand on 2008-06-14
Whenever I accidentally start my computer with killswitch on this happens (see below, notice "UNCLAIMED")
It stays like this even though I enable the wireless with the switch.
In this state I am completely unable to use the wireless and with ifconfig and iwconfig the ath0 module normally used doesn't even show up.

user@macer:~$ lshw -C network
(19:49:06) Ienorand: WARNING: you should run this program as super-user.
(19:49:06) Ienorand:   *-network:0 UNCLAIMED   
(19:49:06) Ienorand:        description: Ethernet controller
(19:49:06) Ienorand:        product: AR2413 802.11bg NIC
(19:49:06) Ienorand:        vendor: Atheros Communications Inc.
(19:49:06) Ienorand:        physical id: 2
(19:49:06) Ienorand:        bus info: pci@0000:09:02.0
(19:49:06) Ienorand:        version: 01
(19:49:06) Ienorand:        width: 32 bits
(19:49:06) Ienorand:        clock: 33MHz
(19:49:06) Ienorand:        capabilities: cap_list
(19:49:07) Ienorand:        configuration: latency=168 maxlatency=28 mingnt=10

Secondly if I switch on and of the killswitch when already started and connected, I also am completely unable to connect again, but this time it doesn't say "UNCLAIMED"

I'm using restricted i.e. madwifi driver (presumably)

Anybody have any solution/suggested further troubleshooting steps?

Additionally, if bug report is due, against what package?

- Arand

---

