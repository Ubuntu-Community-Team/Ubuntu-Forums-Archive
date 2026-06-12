---
title: "got wireless working, but cannot connect to access points"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by awong on 2006-08-04
I got my linksys wusb11v4 working via ndiswrapper, I can detect the wireless network in my house and others around my area, but I cannot connect to my 128bit WEP protected router.  I have my router set as an open system too.  I've been able to connect to the other unprotected wireless notworks in my neighborhood, but only once or twice successfuly.  I've tried to use wifirader, but it isnt working.  And I tried to download GTKwifi from windows to my flash disk, to install in ubuntu, but I get a corrupted file or no permissions to install.  Also have network manger installed.  The few times I did connect I used network manger
Something is wrong especially since I can connect on the other wireless networks and my own when I use windows 98.  

I also tried connecting using the terminal
```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "name of network"
sudo iwconfig wlan0 key open "wep key"
sudo dhclient wlan0 
```

I'm not sure whats wrong, but I havent been able to successfully get on any network.

---

### Post by cantormath on 2006-08-04
> **awong said:**
> I got my linksys wusb11v4 working via ndiswrapper, I can detect the wireless network in my house and others around my area, but I cannot connect to my 128bit WEP protected router.  I have my router set as an open system too.  I've been able to connect to the other unprotected wireless notworks in my neighborhood, but only once or twice successfuly.  I've tried to use wifirader, but it isnt working.  And I tried to download GTKwifi from windows to my flash disk, to install in ubuntu, but I get a corrupted file or no permissions to install.  Also have network manger installed.  The few times I did connect I used network manger
Something is wrong especially since I can connect on the other wireless networks and my own when I use windows 98.  

I also tried connecting using the terminal
```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "name of network"
sudo iwconfig wlan0 key open "wep key"
sudo dhclient wlan0 
```

I'm not sure whats wrong, but I havent been able to successfully get on any network.

I know you said that you dont have wep enabled, but do you have the mac address filtering on, also know as Trusted PCs that are allow to connect?

I personally think ndiswrapper is the last way to go with wireless.  I would rather buy a new card.  But I realize, alot of people cant do that.

I use wifi-radar.  Its in the repos, you can get it in synaptic or add/remove.  It just works better for me.  maybe you would want to try that.

---

### Post by awong on 2006-08-04
well I did recently turn off mac address filtering on the router as it works well in win98.  And I've tried another wireless router a netgear wg311v2, but its a pci2.2 and is incompatible with my mobo.  My only option has been using the linksys.

---

### Post by cantormath on 2006-08-04
> **awong said:**
> well I did recently turn off mac address filtering on the router as it works well in win98.  And I've tried another wireless router a netgear wg311v2, but its a pci2.2 and is incompatible with my mobo.  My only option has been using the linksys.

If mac address filtering is "on" in the router, you do need to add the mac address for the card to your routers mac address access list.

---

