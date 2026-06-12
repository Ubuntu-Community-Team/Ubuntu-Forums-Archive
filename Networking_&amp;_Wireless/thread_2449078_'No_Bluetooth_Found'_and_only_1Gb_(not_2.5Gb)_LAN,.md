---
title: "'No Bluetooth Found' and only 1Gb (not 2.5Gb) LAN, B550-i ROG Strix motherboard"
date: 2020-08-19
forum: Networking &amp; Wireless
---

### Post by andle on 2020-08-19
hi ubuntu forums,


i just  built a new PC and everything went smoothly apart from some networking issues,  hoping someone here can offer troubleshooting advice. 

basically I can't see my bluetooth and my wired networking works slower than expected. Wireless networking seems to work fine. below are some  details:


hardware:


[LIST]
[*]'ROG Strix B550-i' motherboard (BIOS version 1004) 
[*]Intel Wi-Fi 6 AX200 
[*]Intel I225-V 2.5Gb Ethernet 
[/LIST]
software:


[LIST]
[*]'Ubuntu 20.04.1 LTS' operating system 
[*]'Linux 5.8.2-050802-generic' kernel 
[/LIST]

attached is my 'wireless-info.tar.gz', hopefully everything useful is in there.

in BIOS i have disabled fast-boot and have toggled the bluetooth controller enable-disable, those didn't work. i installed the latest BIOS and kernel versions.

let me know if there's any additional info i can provide, thanks in advance!

---

### Post by TheFu on 2020-08-20
Count yourself lucky if the i225v chip is working. Some people here ended up buying $25 Intel PRO/1000 NICs to get wired ethernet working while Intel works on a solution. Do you actually have a router capable of 2.5Gbps connections?  Those wouldn't be the typical home router for $100 or less.

Can't help with bluetooth - I don't use it due to security considerations. Got hacked a few years ago by accidentally leaving a BT driver loaded on a fresh Ubuntu desktop install fully patched the day before. Since then, no BT for me.

---

