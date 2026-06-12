---
title: "Wireguard and tethering via phone."
date: 2019-04-23
forum: Networking &amp; Wireless
---

### Post by Knowles on 2019-04-23
I have an Ubuntu 19.04 laptop (Fresh installed) with an Ubuntu 18.04 server hosted in AWS. I am currently using WireGuard as my VPN installed via "ppa:wireguard/wireguard". 

When I connect to the VPN via a conventional wireless or LAN connection everything is fine, however when I attempt to tether my phone (One Plus 6T) in the UK (on EE) via WiFi or USB this does not seem to work. 

I do not believe it is the phone though for 2 reasons:

1) There is an android application which I have installed and works flawlessly.
2) If I install a virtual machine on the laptop and configure the virtual machine to get its internet via the host (NAT'd) and I install and configure WireGuard on the virtual machine then tether the phone on the host. It works fine.

Any ideas?

---

