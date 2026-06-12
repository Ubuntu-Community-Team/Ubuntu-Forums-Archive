---
title: "PCMCIA Network Problems"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Hav0ck on 2006-12-18
Hey all,

I hope someone can help me out. I am having a problem getting a PCMCIA 3-com Nic working in Ubuntu Dapper on my Laptop.
I have a clean install of Dapper with no extras as I haven't been able to get my network working yet :)
The nic works in a buddies Windows laptop.
The 3-com card is detected and showing up in Devices, however it will not get a IP connection via DHCP. I can specify an IP but I am unable to ping any other computer on my network nor am I able to ping the laptop from any other network computer.
When DHCP is enabled and I do an ifconfig there is no IPv4 IP listed but there is an IPv6 entry.
I think that about covers everything I've tried, Does anyone have any ideas on what the problem might be?

Thank You,
Hav0ck ](*,)

---

### Post by n00b@linux on 2006-12-18
[[COLOR=#666666]Is your device listed [/COLOR]]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards3Com")here:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards3Com](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards3Com)

---

### Post by Hav0ck on 2006-12-18
I'll have to check that when I get home. I believe it was listed on the list, but I cannot be 100% at this time.

---

### Post by Hav0ck on 2006-12-19
well that seems to be the problem. My card the 3com 3C589C Etherlink III is not listed, However when I am in terminal and do a man 3c589_cs it indicates that the 3c589 card is supported as the 3c589_cs.o is the driver for the card.

Can anyone give me any insights into this?

Thanks
-Hav0ck

---

