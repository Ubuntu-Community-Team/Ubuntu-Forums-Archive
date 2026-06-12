---
title: "connection editor being a PITA, 16.04 new install"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by yonnie on 2016-04-28
Trying to create static IP addresses for various connections.  Sometimes it works, most of the time it won't.  Comes back with something about a ping failure.  Message appears mostly meaningless as the numbers given are always different.  Basicly, it's a fault that happens after cancelling the nuisance kdwallet, appears to be default condition.  
The ethernet port cable may or may not be connected at the time of creating the manual static port information and should have no relevance to the failure message.

Perhaps I need to install a networking component that was not installed by default?

---

### Post by Bucky Ball on 2016-04-28
If you have a router serving IPs via DHCP, make sure you set a range for it to serve in. For instance, set the router to serve between 192.168.0.10 - 20 for instance then set your static IPs on the local machines outside of that range. See if that helps.

The ping errors sometimes may mean that sometimes the static IP you're trying to use has already been served by the router's DHCP server.

---

### Post by ajgreeny on 2016-04-28
You can probably also set reserved IPs for devices in the router's configuration; that is what I have done in our household with our 8 connected computers, phones / tablets, printers and Now-TV (Roku) set-top boxes.

No matter what happens the local IPs are always the same.

---

### Post by yonnie on 2016-04-28
The laptop was not connecting to the local network, period, during creation of new IP in connection editor.  The Connection Editor is for internal port settings, not external.  It should not be pinging jackshit during creation of new port settings.
The laptop is being setup to connect to routers for configuration purposes.  I use ethernet to plug into routers and then configure them (routers) for deployment.  To do this, I need to create an IP address in the laptop that will work on the new routers subnet.  (such as setting the laptop IP to: 192.168.0.9 so I can talk to a router on 192.168.0.1, without being concerned with interference with other devices on subnet)  The connection editor on 16.04 fails at this 2 out of 3 attempts.  A little pop-up window says failed, error with ping blah blah blah then some random number and guint blah blah blah.  I've never had this type of failure occur in previous versions of Linux.  This trouble is new to me.  I tried to get a picture of it and by the time I got the camera ready it went away.  I finally got the kwallet to stop its nonsense so now as soon as I hit OK on the connection editor the failure error will display.  This seems to happen randomly about 2 to 3 attempts.  Failure seems to know when I have the camera ready.

14.04 had a different problem with network settings where it would jump to a different IP during router configuration reboots, and especially annoying when using the wifi to connect to another resource at same time as ethernet the laptop would go into a non-responsive mode requiring a reboot (using both wifi and ethernet).  I can't be spending all day waiting for laptop and then router to reboot.

---

### Post by Bucky Ball on 2016-04-28
Well, at least now that's clear ...

Way more involved than first impressions and beyond my expertise. Probably best in future to put all relevant information in the first post. Good luck.

---

### Post by yonnie on 2016-04-28
seems to work slightly better if I don't enter a name for the connection and then go back and edit the name after it works.  Try creating several connections with your 16.04 and see if you get something similar to what I'm seeing.  You should not need a working device plugged into ETH0 while using the connection editor

---

