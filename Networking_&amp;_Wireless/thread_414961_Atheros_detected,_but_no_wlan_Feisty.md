---
title: "Atheros detected, but no wlan? Feisty"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by drifting on 2007-04-20
I am really confused.

I had this working briefly, now for some reason the card does not show up in network config?
According to the restricted drivers it's there, also doing an lspci shows it as being there. 

But when I do an lshw -class Network it states UNCLAIMED

description: Ethernet controller
product: AR5006X 802.11abg NIC

etc..

I thought with feisty that the wireless networking was all sorted? and I did not have to sacrifice virgins, and chant strange command lines to get this going...

Paul.

---

### Post by karhulitos on 2007-04-20
I guess I have the same. I upgraded to Feisty exactly because live CD detected my box 100% and I did wlan with it by only giving my wep key, network manager did the rest.

Now all I get is:

```
-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
```

Any hints?

---

### Post by drifting on 2007-04-20
I have no idea why it's doing this, I even went so far as to install a USB Belkin wireless pen, and would you believe it that worked!

It would appear by all the posts that Feisty is having issues with Wireless, from my experience Linux in general has :(

Paul.

---

### Post by drifting on 2007-04-20
Update.

I removed Kwifi , wifi-radar, and now its working ! Wonder how long for?

Paul.

---

### Post by dstubb on 2007-04-20
> **drifting said:**
> I have no idea why it's doing this, I even went so far as to install a USB Belkin wireless pen, and would you believe it that worked!

It would appear by all the posts that Feisty is having issues with Wireless, from my experience Linux in general has :(

Paul.


I have the same problem here...worked fine in Edgy.

---

### Post by danieltellez on 2007-04-22
> **drifting said:**
> I am really confused.

I had this working briefly, now for some reason the card does not show up in network config?
According to the restricted drivers it's there, also doing an lspci shows it as being there. 

But when I do an lshw -class Network it states UNCLAIMED

description: Ethernet controller
product: AR5006X 802.11abg NIC

etc..

I thought with feisty that the wireless networking was all sorted? and I did not have to sacrifice virgins, and chant strange command lines to get this going...

Paul.

My network state is DISABLED... and I have the same problem.

---

### Post by drifting on 2007-04-23
Well thought I would report back for the hell of it. I found that after a reboot the Athros based chipset card was just too unreliable, and was rather a hit and miss affair,changed back to the USB Belkin and it works without issue.
No idea why?
Paul.

---

### Post by Hallvor on 2007-04-23
I have the same problem. Atheros AR5005G. Worked like a charm for a few days, but now it`s gone from the manager.

---

