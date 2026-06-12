---
title: "Wifi Radar usage question"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by uzd4ce on 2007-02-06
I use Wifi Radar to connect to my wireless network at home with no problems (NetworkManager does not see my wireless card.)  

But for the longest time I couldn't get it to connect to the network at work.  It would see the network, but I couldn't get it to acquire an IP.

Today I figured out that it would connect just fine, but only when I went into the network settings in Admin/Prefs/Networking and manually set up my eth1 settings for my work network.

Am I missing something, or isn't that what Wifi Radar is supposed to do?  I'm not supposed to have to adjust the settings in both WiFi Radar and also Network Settings am I?

Am I supposed to somehow disable the Network Settings from overriding the Wifi Radar settings?

Thanks,
Bill

---

### Post by Floppyjoe on 2007-02-06
On my laptop i had trouble with network-manager not seeing my wireless connection because it was listed as eth1. I changed a eth1 to wlan0 in the file /etc/iftab.
```
sudo gedit /etc/iftab
```
> 
edit

eth1 mac your-wireless-card-mac-address arp1

to

wlan0 mac your-wireless-card-mac-address arp1

Then i removed all other network connecting programs except network manager and disabled all my network interfaces in System/Administration/Networking as is required for Network Manager to work. 

I then rebooted. This will work for an unsecured access point. Wpa encryption will require some extra set up.

---

### Post by uzd4ce on 2007-02-07
Dude, you're the man!

I'd looked all over for advice with my BCM4318 and then your simple suggestion did the trick.  I can now connect just fine at home or at work using NetworkManager, which sees my card with no problems.

Many Thanks,
Bill

---

