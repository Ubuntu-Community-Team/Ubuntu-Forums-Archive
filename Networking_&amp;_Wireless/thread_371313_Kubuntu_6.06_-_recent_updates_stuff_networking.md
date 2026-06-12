---
title: "Kubuntu 6.06 - recent updates stuff networking"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by master_b on 2007-02-26
I'm running Kubuntu 6.06 on ADSL through a modem/Router and ethernet switch.

All networking was running perfectly - ports forwarded where necessary ( ie amule/ktorrent etc)- static IP, no DHCP.

last couple of days amule has been running slowly. I eventually noticed the log message saying that I had Low ID etc.

Checked Modem/Router settings - all ok.

Noticed that SuperKaramba networking applet was not showing throughput or ip.

Checked Network settings to find that IP had changed as was now set to DHCP.

Corrected network settings - manual IP etc, and once again have High ID for amule

It appears that this has occurred sine updates a couple of days ago.

Anybody have any idea how to fix Superkaramba and what were recent updates ?

thanks

master_b

---

### Post by master_b on 2007-02-26
Following on from above -

Just had a brainwave ( Doh!) - forgot that I had swapped 10/100mbs eth card for gigabit card 2 days ago :confused: 

Have been playing with SuperKaramba and trying latest sys monitor thems and finally noticed that system sees new card as ETH1 whereas old card was ETH0.

Input/Output not showing on Superkaramba applet as I guess that system still has config somewhere for Eth0

Help to fix this please.

Meanwhile I'll keep muddling along hoping not to stuff system

master_b:lolflag:

---

