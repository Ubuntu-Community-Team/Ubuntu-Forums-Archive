---
title: "how to connect to wireless with no security"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by evil316 on 2007-11-27
I'd like to know how to connect to a wireless network with no security and no password.  My laptop connects fine to my home network with WEP but I'm trying to connect it at the Childrens hospital which has no security and no password using DHCP.  When I tell it the SSID and no security it finds the network and then comes back with security options and either a key or password for which there is none.  How do I bypass this?  It's as if the network manager has to have a password to connect.  Maybe I'd be better off connecting command line?  If so please let me know how I can accomplish this.

Thanks!

---

### Post by x64Jimbo on 2007-11-28
If it's coming back asking for more info, it's because it thinks there is more. Are you sure the network is unencrypted? It's not like most hospitals to have unprotected computer networks. If you're absolutely positive that there is no security on the network, you can use the command "iwconfig" to do your WiFi bidding. 
sudo iwconfig <interface> essid <SSID>
sudo dhclient <interface>

---

### Post by evil316 on 2007-11-28
Thanks, I'll give that a shot.  The hospital has a doc on how to configure the network.  Nothing for Linux though.  It states clearly that it is DHCP, no encryption or security.  Oddly enough it states that it won't work with Vista, don't know why that is though.  Anyway thanks for the info, I'll give that a try to tomorrow when I'm up there.

---

### Post by evil316 on 2007-11-30
That worked.  THANKS!

---

### Post by x64Jimbo on 2007-12-01
If it says that it will not work with Vista, there is something funky afoot. My guess is that they're using some really outdated equipment or something. Some of the really old equipment has some strange quirks.

---

### Post by evil316 on 2007-12-01
I'm sure it's something like that.  It's the wireless network for patients at Childrens hospital in St Louis.  No encryption or password, probably just an outdated adhoc spotty network for patients and visitors.

---

### Post by ramontayag on 2008-02-24
Hi!  This almost worked for me as well.  The mac at home was having a hard time connecting to the network with the WPA encryption and stuff, so we removed security and stopped broadcasting the SSID.

I did what you posted above, got an IP, but I can't even seem to ping the router.  What do you think the problem is?

---

