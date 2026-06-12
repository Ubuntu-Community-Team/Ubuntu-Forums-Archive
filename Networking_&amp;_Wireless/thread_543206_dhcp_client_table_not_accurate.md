---
title: "dhcp client table not accurate"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by lunaz on 2007-09-04
i'm not sure if this is a problem or not, but the router doesn't show the host names right and oldpos's name never shows up.

[img]http://lunaz.com/pics/dhcp_table.gif[/img]

..and i have 3 comps not 4 :)

when that screenshot was taken i looked at all 3 comp's ifconfig, and had (from memory):

oldpos at 192.168.1.100
badassnes at 192.168.1.101
sux at 192.168.1.117 (why 117?)

just confused about why it'd do wierd stuff like that; i can turn on all 3 again & do more outputs if necesary.

the router is set up with dhcp, and each comp gets their lan address by dhcp too.
sux is connected wirelessly with wep, oldpos & badassness are both wired.

---

### Post by kidders on 2007-09-05
Hi there,


> **lunaz said:**
> the router doesn't show the host names rightIn actual fact, I would be surprised if the things labeled "Client Host Name" are hostnames at all. They are more likely to be DHCP client IDs, which are largely irrelevant. If they served a useful purpose on your network, you would know about it, I'd say.

> **lunaz said:**
> i have 3 comps not 4One of your machines appears to have more than one lease, but that's not particularly abnormal. Unless it's causing you a problem, you can ignore the extra lease.

> **lunaz said:**
> sux at 192.168.1.117 (why 117?)One way of answering that question would be to say "Why not?". Again, it's entirely irrelevant, but possible explanations include:
[LIST]
[*] The DHCP client requested that IP, and the server didn't have any reason to disallow it.
[*] If by asking the question you mean "Why wasn't 192.168.1.102 allocated to that host?", it's worth remarking that only badly designed DHCP servers allocate IP addresses in numerical order.[/LIST] 
I hope that helps answer your questions.

---

### Post by lunaz on 2007-09-05
thanks for the reply :P

i'm not having any problems yet that i know of, just curious. why is a dhcp server badly designed if it gives out the numbers in order?

---

### Post by kidders on 2007-09-05
You shouldn't have any trouble :-)

The only reason I can think of that multiple redundant DHCP leases would be problematic is if your DHCP were dynamically updating a DNS server. In that event, it's conceivable that something that depended on *pedantically* accurate DNS information could misbehave, because sux's reverse name resolution wouldn't be entirely consistent.

Anyhow, it's usual for DHCP servers to assign addresses from a given pool in reasonably random order, to avoid certain issues that can arise in highly loaded environments, where the server is handing out and revoking very large numbers of leases all the time. For small networks like yours, the allocation policy makes no difference, really.

**Edit:**
Incidentally, I should probably add that, if you *want* to, you can have oldpos send its client ID to your DHCP server, for the sake of aesthetics. It won't affect your network's functionality in any way, but it might make your DHCP lease tables easier to read. What OS is it running?

---

### Post by lunaz on 2007-09-06
router runs whatever it came with, i made no changes to the firmware.
sux & oldpos are feisty & dapper server, badassness is edgy & winxp.

---

### Post by kidders on 2007-09-06
In that case, your dhclient configuration is the place to look, just in case you're interested. As I mentioned though, your computers' DHCP client IDs probably aren't used for anything. Changing them would most likely cause more duplicate leases to be issued, however.

---

