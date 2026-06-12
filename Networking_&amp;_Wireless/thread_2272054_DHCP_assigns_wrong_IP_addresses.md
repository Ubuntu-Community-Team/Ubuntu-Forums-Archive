---
title: "DHCP assigns wrong IP addresses?"
date: 2015-04-03
forum: Networking &amp; Wireless
---

### Post by kepar2 on 2015-04-03
Hello!

[COLOR=#333333][FONT=UbuntuRegular]Why does my DHCP server assign wrong IP addresses to everyone in the subnet? I thought the DHCP would start from the first free IP address and next. Like:[/FONT][/COLOR]

[LIST=1]
[*]comp1 - 192.168.100.3
[*]comp2 - 192.168.100.4
[*]comp3 - 192.168.100.5
[*]etc..
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]but my DHCP gives this:[/FONT][/COLOR]

[LIST=1]
[*]comp1 - 192.168.100.3
[*]comp2 - 192.168.100.101
[*]comp3 - 192.168.100.102
[*]etc..
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]what causes this? I thought comp2 should get 192.168.100.4, and not 101.[/FONT][/COLOR]

---

### Post by Doug S on 2015-04-03
Hi and welcome to Ubuntu forums.

According to [the ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/dhcp.html") the assignment from the reserved pool is random, however I don't think (but also am not sure) that is the whole story.
You should have a look at your /var/lib/dhcp/dhcpd.leases file to observe what IP addresses have previously been allotted, and such. I think (but am not sure) the DHCP server will continue to use IP addresses from the pool even if an old lease has expired. Once it has none left it will re-use them. Also, if the same MAC address is trying to obtain a lease, previously long since expiered, it will try to give the same IP address if possible (i.e. available).
On my server all of the possible IP addresses from the pool have been used at one time or another.

You could try deleting your /var/lib/dhcp/dhcpd.leases and starting again.

I saw this question and some others on askubuntu.com that have me thinking that perhaps what you really want is to assign IP addresses based on MAC address, so that any given network device will always get the same IP address and you can use DNS for forward and reverse lookups. That is what I do on my system (the above mentioned pool, is just for guests).

---

### Post by kepar2 on 2015-04-04
> **Doug S said:**
> Hi and welcome to Ubuntu forums.

According to [the ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/dhcp.html") the assignment from the reserved pool is random, however I don't think (but also am not sure) that is the whole story.
You should have a look at your /var/lib/dhcp/dhcpd.leases file to observe what IP addresses have previously been allotted, and such. I think (but am not sure) the DHCP server will continue to use IP addresses from the pool even if an old lease has expired. Once it has none left it will re-use them. Also, if the same MAC address is trying to obtain a lease, previously long since expiered, it will try to give the same IP address if possible (i.e. available).
On my server all of the possible IP addresses from the pool have been used at one time or another.

You could try deleting your /var/lib/dhcp/dhcpd.leases and starting again.

I saw this question and some others on askubuntu.com that have me thinking that perhaps what you really want is to assign IP addresses based on MAC address, so that any given network device will always get the same IP address and you can use DNS for forward and reverse lookups. That is what I do on my system (the above mentioned pool, is just for guests).


thanks for your help. it worked when i deleted dhcpd.leases

---

