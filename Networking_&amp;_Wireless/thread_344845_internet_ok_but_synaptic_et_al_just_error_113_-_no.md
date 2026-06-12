---
title: "internet ok but synaptic et al just error 113 - no route to host"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by eleses on 2007-01-23
Ok, first I am running 6.10 through a Dlink DWL-G700AP access point. 

I have managed to get the Internet working fine - I am typing this on it now - but when I try to use synaptic to update all that happens is that it whips through all the files it should be downloading with the error, '113 no route to host'. 

I have all the repositories selected in software sources.

I managed to get the internet working by disabling the ipv6 protocol using : 

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6 

in the etc/modprobe.d/aliases file

If you need any more information just ask and I'll provide it - to be frank I haven't really a clue what I'm doing as I'm new to Linux and am trying to work things out as I go.

I have read that it could be a DNS problem but do not really know enough about it all to sort it out. Any advice would be greatly appreciated.

---

### Post by [L2G] Slapshot on 2007-01-24
Hi Eleses

Just check this thread ( I know I know ) it's a Mepis Linux thread, but I remember a guy having the exact issues ages ago with D-Link firmware in the router ( think it was in Australia ) not allowing DNS passthrough. He complained to D-Link and they updated the firmware to help linux users. In the thread he gives quite a bit of detailed info  and actually what D-Link do solves it.

Thread is 

[http://www.mepis.org/node/10306]("http://www.mepis.org/node/10306")

Hope this helps
Jacko

---

