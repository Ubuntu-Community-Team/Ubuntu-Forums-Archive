---
title: "Network-admin and static ip address"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by stefano.fraccaro on 2008-03-26
Hi,
    in Ubuntu 7.10 and 8.04 beta I have a problem when change from the default roaming mode to static IP address. I can set the ip address, network mask and gateway ... the file /etc/network/interfaces is correctly updated but the new file configuration is not reloaded, I must run 'sudo /etc/init.d/networking restart' from a terminal to use the new ip address.
This is a big problem because I frequently use Ubuntu in live mode ... on other words, I can't reboot the system for reload new interface parameters.
I'm the only one that has this problem? From the terminal all works fine... the only problem seems to be the GUI.

Any ideas?

Best regards 
Stefano Fraccaro

---

