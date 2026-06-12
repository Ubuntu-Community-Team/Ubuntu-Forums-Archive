---
title: "pc conflict in network"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by eldude2 on 2013-10-23
Me and my brother had installed ubuntu (12.04) and sometimes we cant get both the computers linked to the home wi-fi network.

it seems that just one pc at a time can be connected (the first to be connected to the network).

in one of the pc's the eth 1 does not appear in the ifconfig.

any suggestion or solution?

whe are both fairly green on using linux in general and tried everything we know at the moment.

cheers

---

### Post by xiccarph on 2013-10-23
This is probably not an Ubuntu problem.
Your computers are probably trying to connect through DHCP (where the wi-fi network, the router) provides an IP address out of a pool of possible addresses.
If the router is configured to only allow one DHCP address (not real likely, but possible) it could explain that problem.

Here are some questions you should try to answer.
Will either PC connect to the network if the other is off?
What IP address and other connection information is listed in the Network Connection properties of the connected PC?
Is it the same for both PCs?
Have you ever administered (logged on) to your home router?
Did you configure the PCs with the same static IP address (not using DHCP)?

---

### Post by eldude2 on 2013-10-24
the answers, in order, are:

yes.
all same except the ip adress. one is .2 the other .3 .
it is answered above; no.
yes to both pcs.
no, ill try to do that (in spite of not knowing how it might be easy to find).

thank you for your time.

---

### Post by eldude2 on 2013-10-24
i've tryed to set it static. The same problem occur.

the problem, as far as my brother told me, appears to happen ever since the recomended updates are done.

---

### Post by xiccarph on 2013-10-24
You don't want them to be set to static.
Have them set to DHCP so they will take any available ip address offered by the router.
What type of router are you using, did you manage to get to the administration interface (usually done through a web browser on a machine connected, by wire, to the router)?
Are both of your machines connecting to the router by wire, or wireless, or a combination?

---

