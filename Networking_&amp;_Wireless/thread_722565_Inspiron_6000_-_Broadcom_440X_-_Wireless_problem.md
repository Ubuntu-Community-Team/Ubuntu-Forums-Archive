---
title: "Inspiron 6000 - Broadcom 440X - Wireless problem"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Saxpest on 2008-03-12
Hi,
 I'm still pretty new to Linux in general. I'm still running ubuntu from a live disc, i've got mandriva partitioned away but ubuntu has blown me away and I want to switch except I cant get the internet to work. I've got a Dell Inspiron 6000 and its running the Broadcom 440x wireless card. The strange thing is it recognises the wireless card and it also comes up with my home network but when i input the wep key and let it do it's thing nothing happens. I've tried the Wi-Fi Radar application and that does pretty much the same thing. Any help would be appreciated. Wireless works in both windows and mandriva so it's nothing to do with the hardware!
Thanks muchly.

---

### Post by wormser on 2008-03-12
I have a 6000 with a BCM4309 wireless card.  The ethernet is BCM4401.  What is the exact model of your wifi card?

```
lspci | grep -i broadcom
```

How did you install it?  I installed mine with System> Administration> Restricted Drivers Manager and it works fine except for a bug on shutdown.

---

### Post by Saxpest on 2008-03-12
Hey, sorry, well in Mandriva's hardware ID section it says its got:

    BCM4401-B0 100Base-TX
 AND
    Intel(R) PRO/Wireless 2200BG

Not sure which one is what i'm looking for and what the hell i can do with the info anyway! Could be one is the ethernet card and the other is the wireless?
 Cheers!

---

### Post by wormser on 2008-03-12
> **Saxpest said:**
> Hey, sorry, well in Mandriva's hardware ID section it says its got:

    BCM4401-B0 100Base-TX
 AND
    Intel(R) PRO/Wireless 2200BG

Not sure which one is what i'm looking for and what the hell i can do with the info anyway! Could be one is the ethernet card and the other is the wireless?
 Cheers!

The BCM4401 is the ethernet and the Intel is the wireless.  I would recommend removing the WEP key and connecting first.  Once it connects then add the WEP key.

---

### Post by Saxpest on 2008-03-12
Right, update, i've got it connected to the network and the bars showing signal strength are up, but the information in the network manager is telling me that the ip and subnet mask etc is all 0.0.0.0.0 and i still cant get a webpage open. Any ideas? I got it recognising a signal first trying to manually configure a connection and then going back to the automatic and it works. The signal strength is even relative to the distance from the router so its defnintely kind of connected???
Cheers

---

### Post by PaganBlasphemy on 2008-04-04
I have a Dell Inspiron 6000 with that Intel chipset and I've never had a problem with the wireless (although the network management was less than intuitive for me when I started).  

To simplify troubleshooting, I'd sug
 If that doesn't do anything for you (you still aren't getting an IP address from your routegest first turning off encryption for a couple minutes to see if that is the source of the problems.  I've read that in general support for encryption can be troublesome (just as it often is in Windows) although I haven't ready anything specific about this Intel chipset.

 If that doesn't do anything for you (you still aren't getting an IP address from your router) do you have some kind of access management going on it, where it only hands out IP address to MAC that are in an access list?  

The wireless connection is independent from the rest of the networking.  The way it breaks down roughly is:
1) your computer asks the wireless access point for a connection
2) your computer asks the router for a LAN IP address and other networking information
3) your computer asks the internet for information

So, you seem to have step #1 complete, but perhaps a problem with the encryption is preventing #2 from happening.

When you were tweaking the settings manually, you did make sure to return all of the settings where they originally were?  Automatic DHCP or Roaming Mode enabled, and so on and so on?

---

