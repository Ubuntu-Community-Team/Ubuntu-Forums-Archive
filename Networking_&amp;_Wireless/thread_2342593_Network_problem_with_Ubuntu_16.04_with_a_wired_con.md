---
title: "Network problem with Ubuntu 16.04 with a wired connection."
date: 2016-11-08
forum: Networking &amp; Wireless
---

### Post by beanteam1 on 2016-11-08
I am running a HP DL360 G6 with Ubuntu 16.04 and up until a day ago everything was running fine with the server. The power was scheduled to be taken off for a quick moment so i ensured that i shut down the server prior to this. Well, once i brought the server back online, i have been having problems with my networking. I am using a TP-LINK R600VPN router that is wired through to my server. The router and internet service is still working fine for my desktop and wifi is still up and running with my laptop and other devices.

Since I have been working on this issue, I have ran sudo lshw -c network and found out that all my networks are displaying as disabled (I would paste the log here but the problem is on my server). After running dmesg, i came across;
device virbr0-nic entered promiscuous mode
virbr0: port 1(virbr0-nic) entered listening state
virbr0: port 1(virbr0-nic) entered listening state
virbr0: port 1(virbr0-nic) entered disabled state

and

bridge: automatic filtering via arp/ip/ip6tables has been depracated. Update your scripts to load br_netfilter if you need this.

Nothing else really stood out. I am trying to troubleshoot this issue to the best of my general knowledge of Ubuntu at the time being. If anyone has any ideas I would greatly appreciate it and if any more information is needed from me that I may have left out or just didn't know about, please let me know and I will try my best to provide it.

Thanks in advance.

---

### Post by beanteam1 on 2016-11-09
I am still trying to solve this issue. Does anyone have any suggestions at all?

---

