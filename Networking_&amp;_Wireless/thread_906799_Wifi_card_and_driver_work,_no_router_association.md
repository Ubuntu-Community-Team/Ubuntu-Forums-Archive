---
title: "Wifi card and driver work, no router association"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by jeremias on 2008-08-31
First time post here; I'd appreciate any help from anyone!

I've installed Ubuntu 8.04 on a Dell Latitude C610 with a built-in wireless 802.11b card.  The orinoco driver was loaded automatically, and allows me to use iwlist to scan and display wireless networks, including my home network.  Running iwconfig shows my essid, but access point is "None".  

I am using 128-bit WEP encryption, but even when switching to an open network, I have the same problem, no association.  I took the laptop to an open network at McDonald's and it worked fine!  So there is something wrong with my setup at home.  I have a D-Link wireless N gigabit router running in mixed 802.11n, 802.11g,l and 802.11b mode on channel 2.  DHCP is enabled, and the only authentication options are "both" and "shared".  I haven't tried shared yet, but from other threads it seems that has the least chance of working.  The laptop gets no dhcp offers from the router when running dhclient.  I can ping the loopback device successfully.

What am I missing???

---

### Post by james_vanb on 2008-08-31
Try this to get connected - When you boot and the network manager is looking for a connection (The 2 dots in upper right of toolbar) - Open a terminal and run the following:

```
sudo iwconfig wlan0 key "hex key"
```

Where "hex key" is the 26 character key for your router.  See if that at least gets a connection.

---

### Post by Shiv4m on 2008-08-31
I had the exact same problem as you, since you just got ubuntu for the first time you need to update it, you need another way of getting to the internet such as using a Ethernet cable. When you connect the Ethernet cable you will get all the updates and ubuntu will automatically recognize what new drivers to add such as nvidia and the wireless card. 

Try to do these things and I am sure it will work!

When you get access to the internet through Ethernet go to to System>Admin>Update Manager, there will be around 200 updates for you!

---

### Post by jeremias on 2008-09-01
Thank you for such quick responses.

James, as far as the command line goes, I have done as you asked a few times before with some of the other options as well.  Tried it exactly as you typed it, (with my key of course), to no avail.  However, I'm not sure what you were talking about with the two dots when booting.  The upper right toolbar just has the wireless network manager icon, which I can rightclick on and get the option to edit wireless networks, but the list is empty, and I can't add any there.

I finally attempted to connect directly using ethernet, and lo and behold I have the same issue: dhcp seems to not work.  Running ifconfig displays an inet6 address for eth0 (wired connection) and eth1 (wireless), and an inet address for eth0:avahi and eth1:avahi  Can someone explain what the difference is?  And why would my router not be offering an IP address to this computer under wired AND wireless?

Needless to say, I was not able to update Ubuntu as Shiv4m suggested.

---

### Post by james_vanb on 2008-09-01
> **jeremias said:**
> First time post here; I'd appreciate any help from anyone!

I am using 128-bit WEP encryption, but even when switching to an open network, I have the same problem, no association.  I took the laptop to an open network at McDonald's and it worked fine!  

Turn encryption off at router - See if you can connect.  It worked at McDonalds - Should work at home with encryption disabled.  May have to reboot.

> **jeremias said:**
> However, I'm not sure what you were talking about with the two dots when booting. The upper right toolbar just has the wireless network manager icon, which I can rightclick on and get the option to edit wireless networks, but the list is empty, and I can't add any there.

In roaming mode, the upper right will show 2 dots with circular arrows showing attempt to connect.  Since you don't see this, sounds like you have already manually configured.  Left click on Network Manager and click "Manual Configuration". Unlock and set Wireless for roaming for now.  Left click Network Manager and see if you can find your router (Assumes encryption has been disabled).  Click to connect.  You may have to reboot if no connection.

Wired connection well supported in Ubuntu - Did you try a reboot with wire connected?

First try to connect and then deal with encryption.

---

### Post by jeremias on 2008-09-03
Just wanted to touch base about this, since I didn't get a chance to try everything tonight.  I seemed to have gotten a connection that showed up on the router for a few minutes, but never had any internet working.  Running iwconfig listed an access point, but the weird thing is that the address that was listed was NOT my router's MAC address.  Isn't that what the access point address is supposed to list with iwconfig?  Anyway, I will attempt the rest of your suggestions tomorrow or Friday, and reply with the results.  Thank you!

---

