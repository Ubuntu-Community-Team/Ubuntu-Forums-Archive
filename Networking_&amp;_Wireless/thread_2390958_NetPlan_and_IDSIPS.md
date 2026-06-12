---
title: "NetPlan and IDS/IPS"
date: 2018-05-04
forum: Networking &amp; Wireless
---

### Post by Etheridian on 2018-05-04
I'm getting used to netplan in Ubuntu Server 18.04, and configurations for simple, bridged setups are easy enough. However, I've run into a bit of a snag when attempting to have it configure interfaces for Snort: How do I get netplan to enable promiscuous mode on the interfaces?

For ifupdown, it was just sending a call for iproute2 to turn it on: 
```
up ip link set $IFACE promisc on
```

Is there a way to do the same with Netplan?

---

### Post by fun71m3 on 2018-05-27
Did you ever get an answer to this question? I'm running into the same issue in my lab environment and haven't been able to find a sufficient answer. I managed to get promiscuous mode enabled by running:

```
ip link set ens192 promisc on
```

But it won't persist through reboots.

---

### Post by wrlsfanatic on 2018-07-16
FYI, I just confirmed with an Ubuntu developer that promiscuous mode is not currently supported by netplan and it is not currently on their roadmap. His suggestion:

> [COLOR=#500050][FONT=Arial]On 18.04, we install networkd-dispatcher (see [/FONT][/COLOR][https://netplan.io/faq#use-pre-up-post-up-etc-hook-scripts](https://netplan.io/faq#use-pre-up-post-up-etc-hook-scripts)[COLOR=#500050][FONT=Arial]) which will [/FONT][/COLOR][COLOR=#500050][FONT=Arial]allow you to run any further command you might need to finish the [/FONT][/COLOR][COLOR=#500050][FONT=Arial]configuration of services / interfaces. That should allow you to make [/FONT][/COLOR][COLOR=#500050][FONT=Arial]sure 'ip link set ens192 promisc on' will persist across a reboot.[/FONT][/COLOR]

---

