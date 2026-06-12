---
title: "Weird network problem after latest updates"
date: 2018-01-29
forum: Networking &amp; Wireless
---

### Post by tps-mail on 2018-01-29
Hi Folks, I am running Ubuntu 16.04, with Mate Desktop on an ASUS motherboard, with an AMD FX-8370 8 core CPU. 
Handling networking via interfaces file, since that's the way I've been doing Debian systems for the last 15 years or so. Network Manager is not installed. IP address is static.
Yesterday (1/27/2018), I updated the latest packages, and linux-firmware and the 4.4.0-112-generic kernel was installed, and I rebooted after the kernel upgrade.

Ever since then, my network has randomly gone away, to the point the lights go out on the NIC ( I have 3 NICs in the machine, and this happens with each one), to the point ethtool tells me there is no link. Disconnecting the cable from the computer or switch end will usually restore the network... for a time. It'll then drop out at some random time. It's not load dependent, it just stops. syslog simply states the NIC is down. Nothing in dmesg of note.

Has anyone else experienced this, or seen this reported? I've groogled my fingers off... now I come to the smart people for the answers. I'm pretty sure I'm doing something wrong, I'm just too close to the issue at this point.

---

### Post by tps-mail on 2018-01-29
I thought this may have been a buss hardware issue, so I connected via a 1G USB network dongle. I was hopeful after the system staying connected for about 8 hours, but then it dropped off with the same manner.

---

