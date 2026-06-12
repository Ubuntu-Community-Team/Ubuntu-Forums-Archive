---
title: "local ethernet works only when dsl is connected"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by riamoh on 2008-08-26
hello all,

i am pretty new to linux and to ubuntu. i have wired lan setup (four machines) as well as a dsl connection that is shared among all machines via a switch.

the phone lines, however, are pretty bad so the dsl connection keeps dropping quite frequently. The problem is that when the dsl connection is dropped, access on the local lan also goes with it. could anyone help?

i'm pretty much a novice, so i'm pretty sure that there are some basic settings that i have not configured. Any help would be excellent.

Also, I'd like to add that when I try to configure my eth0 i get an error message saying that the interface does not exist.

---

### Post by jigsaws on 2008-08-26
Tell us more about the lan configuration - IP, netmask, etc.
Is the switch standalone or it is dsl router with switch? What model?

---

### Post by riamoh on 2008-08-26
It is a standalone baylan switch. The DSL modem is Zyxel and is connected to the switch. As far as IP, Netmasks go, there are no static ips configured as the DSL provider configures the IPs automatically. The only configuration is the DSL providers primary and secondary DNS.

I did not reconfigure any network settings upon installation since ubuntu 8.04 worked right out of the box - the internet and the lan (after doing the sharing bit) was connected. It was only when the DSL went down that I realized that my LAN was not working.

I'm assuming the problem lies with the fact that the network is by default using the DSL provider's DNS to figure out the machines that are on the network - when the DSL itself is down it simply can't do that - hence the issue.

Somehow, I'm assuming that workgroups will somehow be involved in the solution.

Thank you for your replies!

---

