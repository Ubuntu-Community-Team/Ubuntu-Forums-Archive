---
title: "dell d410 not showing or connecting towireless networks"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by jamaas on 2006-12-14
When I click on 
System>Administration>Networking

and try to check for and/or connect to a wireless network
by clicking properties, it won't show me any wireless networks, even though I know several are available.  I know this was an issue when Edgy was first released, can anyone tell me if has been fixed and how to fix it, or what is the best alternative to use to find networks when travelling?

thanks

Jim

---

### Post by sirozha on 2007-01-30
You have to make sure you have installed the following packages: 

wpasupplicant
network-manager-gnome

Then, edit the "/etc/default/wpasupplicant" file and make sure ENABLED=0 is there. 

Reboot your laptop, and you should be able to use the Network Management icon to connect to wireless network.

---

### Post by jamaas on 2007-02-01
Thanks Sirozha,

Both of those packages were loaded.  I don't have the file you suggest editing but do have 

/etc/network/if-post-down.d/wpasupplicant
/etc/network/if-pre-up.d/wpasupplicant
/etc/network/if-down.d/wpasupplicant
/etc/wpa_supplicant/ifupdown.d/wpasupplicant

Anyone hazzard a suggestion about value of editing one or all of these?

Thanks

Jim


> **sirozha said:**
> You have to make sure you have installed the following packages: 

wpasupplicant
network-manager-gnome

Then, edit the "/etc/default/wpasupplicant" file and make sure ENABLED=0 is there. 

Reboot your laptop, and you should be able to use the Network Management icon to connect to wireless network.

---

