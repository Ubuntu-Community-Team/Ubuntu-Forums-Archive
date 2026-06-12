---
title: "DWL-G650 and 108mbps"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by radcc07 on 2007-04-05
I currently have a DWL-G650 Version B (I believe) wireless card setup with my laptop.  I am able to successfully connect to my router with the madwifi driver and WPA.  The issue I currently have is that I don't seem to be hitting 108 mbps (at least from what I can tell with kWifiManager).   If I use this card in my windows work laptop, it can hit 108mbps just fine.

Is there anyone who's able to get speeds of 108mbps with their DWL-G650?

---

### Post by radcc07 on 2007-04-17
Well I was able to solve my issue.

Basically, I blacklisted the ath_pci module/driver - good driver but I couldn't get it to run at 108mbps speeds (according to experience and KWifiManager)

Then I loaded the windows driver for the card - net5211.inf - using ndiswrapper.  I then started the ndiswrapper module and set it up to load on startup.

Since I also use WPA in my network, I ran the wpa_supplicant tool and set the driver to wext.  Now I am able to reach about 108mbps according to KWifiManager as well as from tests I did with streaming video over the internet.

The only issue I'm seeing now is that both Gnome Network Manager and KWifiManager show 0 signal strength even though I am connecting to the network and internet.  Oh well, minor inconvenience.

---

### Post by Shay Stephens on 2007-04-17
> **radcc07 said:**
> I currently have a DWL-G650 Version B (I believe) wireless card setup with my laptop.  I am able to successfully connect to my router with the madwifi driver and WPA.  The issue I currently have is that I don't seem to be hitting 108 mbps (at least from what I can tell with kWifiManager).   If I use this card in my windows work laptop, it can hit 108mbps just fine.

Is there anyone who's able to get speeds of 108mbps with their DWL-G650?

I have that card and it has been working just fine.  I am using the default driver I assume because I have never had to specifically load a driver for that card.  I am running gnome, not KDE.

---

### Post by radcc07 on 2007-04-19
How can you tell the if you're getting 108mbps?  I'm using gnome as well, but couldn't figure out how to tell what my actual speed was at.  With KWifiManger, it has an indicator that gives an idea of the wireless speed (0, 11, 54, 108, etc).  With the madwifi driver, I always seemed to be at 54.  When I did the ndiswrapper method, it shows as 108.

---

### Post by spd106 on 2007-04-19
Try a speed testing utility such as iperf, or time a large file transfer.

It is true the madwifi doesn't support all of the features of the windows driver, I'm not sure but I think this is one of those.

---

