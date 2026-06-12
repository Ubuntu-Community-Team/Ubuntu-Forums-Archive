---
title: "Ubuntu 20.04 Network not working"
date: 2024-07-24
forum: Networking &amp; Wireless
---

### Post by jonathanubian on 2024-07-24
I run Ubuntu 20.04, never had any issue like this with this version.

Last time I used the computer was last night, this morning I found out there is not Internet in my computer. I checked the cable and everything is fine, checked my phone and it has WiFi Internet. Checked the router and it's fine.

Checking my computer I can see the network manager only shows VPN and network proxy options, no mention to ethernet network.

I wish I could upload photos. 

Any help please?

---

### Post by currentshaft on 2024-07-24
What type of computer? Brand, model, version, etc.

Is a network interface recognized? lspci | grep -i "network\|ethernet"

Also check for errors in the output of sudo dmesg

---

### Post by jonathanubian on 2024-07-24
HELLO currentshaft. Many thanks for your answer.

The computer is homebuilt.

CPU Intel 10th gen. I3

Motherboard is Aorus B460M PRO

32GB RAM

1TB SSD

The output FOR exactly this command lspci | grep - I "nerwork\ethernet":

00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (12) I219-V

About the output for sudo dmesg: I can't see any red highlighted error message apart from 

x86/CPU: SGX disabled by BIOS.

But that message has been displaying since first time I built the computer and installed this ubuntu version.

---

