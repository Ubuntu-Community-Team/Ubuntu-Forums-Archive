---
title: "Network Manager Won't Activate VPN"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2007-10-09
I'm confused on multiple levels. After a fresh Feisty install, not upgrade, I cannot connect to my VPN. I could in 6.06 using pptpconfig, not network-manager. 

I freshly installed Feisty after successful 6.06 --> 6.10 --> 7.04 upgrades, because I had read some notes indicating that a problem in pptpconfig and/or network-manager vpn had been fixed. (I'm a bit confused as to which one it was.) I also did a fresh install, because modules.conf looked weird to me. Modules appeared to be loaded from different places. 

I have tried configuring network-manager-vpn, and get this error:

Oct  9 18:01:14 slapazine NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN. 

Also, pptpconfig won't work after 6.06 due to what is thought to be a PPP problem. 

Another point of confusion in network manager is I cannot get to the VPN menu without my built-in ethernet card enabled, even though I am using wireless.

I'm certainly not afraid to test this stuff. I did back out of building an old version of PPP, though; I opted instead for a new installation. If anyone has any ideas on how to proceed, I would appreciate the help.

Edit: 10/13/2007
-----------------------
This all works -- and works quite well -- when I have a wired connection and not using the wireless connection. Being a built in device, it shows up in ifconfig. I'll keep testing to try and find out how this would work properly.

---

