---
title: "pppoe"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by Mar1K on 2006-11-17
hello all,
i just joined the ubuntu community forums and maybe i will be able to help.
i installed ubuntu on my laptop fujitsu siemens and couldnt connect my pppoe connection for more than few minuts.
the solution for me was the following:

run terminal and try the following

sudo -s -H <password for root>

chmod 777 /etc/ppp/pppoe_on_boot

display the pppoe_on_boot and replace the last line that says:

exec call ppd dsl-provider

witht the following

exec pon dsl-provider

it worked fine with me, i hope you enjoy ubuntu now.

---

