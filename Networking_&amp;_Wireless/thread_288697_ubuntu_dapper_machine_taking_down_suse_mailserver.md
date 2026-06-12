---
title: "ubuntu dapper machine taking down suse mailserver"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by gundog on 2006-10-30
We have a soho network with about 5 machines. One is a SuSE 10.1 mailserver. This has worked without error for about six months (since it was set up). However, when I plug my notebook (recently converted to Dapper) into the network the mail server starts sporadically disconnecting and reconnecting to the network. Over about a week I have noticed that the mail server's instability seems to be directly linked to whether the notebook is plugged into the network.

The network was set up by a friend who came and had a look and left scratching his head and mumbling something about IPv6.

I wondered if anyone else had experienced anything similar?

---

### Post by lynxus on 2006-10-30
Could be an IP conflict. Or maybe a MAC address conflict.( probably not )

Chekc the IP settings for your dapper machine.. Maybe put the IP up one digit and see if that helps.

Also check the IPV6 settings on dapper, However i doubt your network is fully ipv6 so this shouldnt cause an issue.

---

### Post by gundog on 2006-10-30
I did check that there is no MAC addresses conflict. I've now forced the server to use a specific IP address and banned the switch/router from assiging any addresses in a range containing that address to any other machines. That seems to have solved the problem. Hopefully it will not reoccur.

Many thanks

---

