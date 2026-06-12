---
title: "Netgear FVS318 VPN Router with ProSafe VPN client"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by scottlpatterson on 2006-11-29
I'm trying to convert my father's home PC to using Linux and connecting to his work PC via VNC through a VPN is the last thing I need working. I'm very familiar with Linux (10 years+ exp), but, am a software guy and don't know much about networking, so, please be explicit when replying.

My father's home PC has Kubuntu 6.10 installed with a working internet connection. He would like to be able to VNC to his work PC (Windows XP) so he can work from home. His company uses a Netgear FVS318 Router for the VPN. His previous computer used ProSafe VPN software to establish the VPN connection. So, how do I establish the same connection, but, using Linux?

---

### Post by Matty2006 on 2007-05-11
I about to attempt this myself and will let you know when I figure it out.. I hope to get connected to a prosafe fvs338. Our router is running OS v2.x. 

The Router OS 1.x is pretty crappy (not user friendly and varied vpn performance) and flaky. Netgear's 2.whatever OS is much better than what these routers likely shipped with..

to use is VNC a VPN is not required but it is more secure if it is setup this way. the super easy way to get him connected is to have them port forward him his pc's IP address if he hits the routers IP with VNC. However, most admins and larger companies are not likely to start opening ports on their firewall/routers without good reason it at all. So then vpn becomes the other option.

Netgear does a fantastic job at making VPN setup confusing as hell. It took me about a day or two just to get the windows client to work right (documentation is not totally correct).. The main thing is that you need a VPN client that supports IPsec tunneling. I am pretty sure this is the default VPN setting on your prosafe router.  I will post again if I can figure this out in linux.

Once the vpn is working then vnc and rdp can be used to his his work machine.

-Matt

---

### Post by gfunkdave on 2007-11-29
Did anyone ever figure out how to do this? I'm a brand new Ubuntu user trying to set up VPN into a FVS318 router.

I'm using KVpnc and raccoon, and the settings *seem* ok, but I'm getting errors about failing to bind to an address and really don't know what I'm doing. 

I have things working with the ProSafe client in Windows.

Thanks for any help!

---

### Post by gfunkdave on 2007-12-01
Bump...anyone?

---

### Post by acl123 on 2007-12-05
I would also like to know how to do this.

---

### Post by yochaigal on 2007-12-14
I would also like to know how to do this.

---

### Post by mutrax on 2008-01-08
Same here, Does anyone have a linux vpn client running to a netgear fvs318 router, to access smb shares behind the router?

Thanks in advance,
µ

Any pointers toward the right direction are welcome![-o<

---

### Post by leupi on 2008-05-10
OK, my turn to bump...

Has anyone figured out how to use a Linux workstation in a VPN with NG fvs318 router? I just bought a new router and am running Ubuntu 8.04.

Thanks,
Todd

---

