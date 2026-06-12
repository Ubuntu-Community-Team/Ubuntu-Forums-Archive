---
title: "help: tow NIC but no eth0"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by whiskey29 on 2008-03-13
Hi everybody,
I have a server which I'm trying to make into LTSP server for my office.
SO I add another NIC gigabit with realtek chipset which I will use as a connection for the LTPS client (connect to gigabit switch). While the onboard NIC is for accessing the internet (connect to my router).

Onboard is Nvidia MCP61, add on is realtek RL-8169

I installed gutsy alternate CD to make use the RAID instantly.

Problems are :
1. the add on NIC is installed as eth1, But the onboard is eth4 and keeps changing on every reboot, to eth5, eth6 randomly, as I'm typing this eth8. No eth0 present

2. When I login ubuntu, nm-applet will by default try to connect to the add on NIC. I have to manually switch it to onboard NIC to get internet working.

any advice is very much appreciated.

---

### Post by handydan918 on 2008-03-13
It's been a while, but I fought with that nvidia chipset and lost. Bought a $5 NIC instead. 
Try it. You'll like it.

:)

---

### Post by larry007 on 2008-03-13
you don't need two NIC's to set up LTSP.  As for that chipset, just disable the onboard NIC i n the BIOS and use your new card instead.  All should be well afterwards...

---

### Post by whiskey29 on 2008-03-13
THanks for the input.
I'll try the 1 NIC.
So I found the culprit. I need to explicitly set the MAC address in BIOS.
So it's not jumping around eth anymore, but the onboard NIC won't register as eth0 but eth1.

I ended up using another NIC which occupy the precious pci slot but it install just fine now.

---

