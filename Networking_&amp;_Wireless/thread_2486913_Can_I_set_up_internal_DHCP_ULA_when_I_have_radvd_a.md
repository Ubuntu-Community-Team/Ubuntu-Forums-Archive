---
title: "Can I set up internal DHCP ULA when I have radvd assigned addresses?"
date: 2023-05-16
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2023-05-16
OK, I managed to solve some problems mentioned in the other [thread]("https://ubuntuforums.org/showthread.php?t=2486476").
Current setup.
No changes in the Netplan (separate story, I hate it).
Right after setting accept_ra to 2, I'm starting isc-dhcp-client, requesting a prefix:

[COLOR=#000000]dhclient -6 -v -P --address-prefix-len 64 eno1

[/COLOR]Interestingly enough, systemd-networkd dhcp client, which requests a single ipv6 address, fails after address expires, and I don't have an ipv6 address on WAN interface anymore. But everything works fine, so I don't worry about it so far.

I think of adding a script, which would change radvd prefix if it changes, but so far, Comcast allocates the same prefix to me all the time.

What I want to do now, is to set up ipv6 internal DNS (AAAA and PTR). Because radvd advertises random addresses and clients don't report their addresses to BIND, I'm thinking of setting up ULA addresses for internal communication, which would be reported to BIND.
And here is the question: how do I set it up? I need some machines (firewall, secondary DNS server, my main desktop) to have static addresses and serve DHCP addresses to other clients. Let's say I set up static addresses in Netplan/Network Manager. Would it interfere with addresses advertised by radvd?

---

### Post by Alex_Filonov on 2023-06-06
Found out that ULA is useless. Oh well, ipv4 for internal communication works great.

---

