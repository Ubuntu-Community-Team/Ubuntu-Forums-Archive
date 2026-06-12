---
title: "Adding IPv6 addresses, only 2 get added"
date: 2018-06-14
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2018-06-14
i am trying to add a large number of IPv6 addresses to [FONT=courier new]eth0[/FONT] but only 2 actually get added.  so i reduced it to just trying to add 3 and still only 2 get added.  i am adding these in the [FONT=courier new]/etc/network/interfaces[/FONT] file.  below these 3 IPv6 [FONT=courier new]iface[/FONT] statements is one to make an IPv4 alias [FONT=courier new]eth0:1[/FONT] and that one also works.  i can manually ad IPv6 addresses with the command [FONT=courier new]ifconfig eth0 add the:long:ipv6:address[/FONT] for each of many addresses (tested 64 of them) and they all always get added OK.  the problem is when i reboot. it comes up with no more than 2 IPv6 addresses no matter how many i configure. [FONT=courier new]/var/log/syslog[/FONT] has no messages identifying the addresses that don't come up.

this is Ubuntu Xenial 16.04.4 LTS server edition (no GUI).

how am i supposed to get more than 2 IPv6 addresses, permanently, before services like the web server and database come up?

what program reads this file and skips over IPv6 stuff after it does 2 of them, but continues on for more IPv4 stuff?

---

