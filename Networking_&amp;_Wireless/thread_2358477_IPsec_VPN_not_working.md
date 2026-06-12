---
title: "IPsec VPN not working?"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by zlyspl on 2017-04-14
Let me begin by saying that i am an amateur at Linux and still learning.

1.) Recently I deleted my dual boot windows 10/Ubuntu Gnome 15.10 and reinstalled my computer with Ubuntu Mate 17.04

2.) All my software are up to date.

3.) Installed Cisco Ipsec software (sudo apt-get install network-manager-vpnc -y

4.) Went to edit connections -> Add connection -> Cisco Compatible VPN -> Create

and I get the following error : Could not load editor VPN plugin for 'org.freedesktop.NetworkManager.VPNC' (missing plugin file "/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-vpn-plugin-vpnc-editor.so")

Are there any solutions for this? Thanks



Solved, 

All I needed to do was sudo apt-get install network-manager-vpnc-gnome

---

