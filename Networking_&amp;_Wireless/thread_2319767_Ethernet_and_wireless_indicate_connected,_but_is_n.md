---
title: "Ethernet and wireless indicate connected, but is not"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by yonnie on 2016-04-07
HP Elitebook 2740p, runing 14.04, kept upto date.

I need to use this thing to connect to multiple devices as a work-tool.  Lately it seems that it gets confused and then quits connecting and I have to reboot to regain control of ports.  Problem seems to happen when I update settings in the remote device and then it reboots and after reboot the port on the elitebook will not re-establish contact even after correct subnet has been set.  

Using the network control panel to establish connection settings seems to just quit.  Window menus and settings seem to function as normal, but no effect takes place.  This problem

This Elitebook might as well be a brick when I have to spend more time with waiting for it to reboot than I spend working on the remote devices that have settings to be made.  I've found my smart-phone is more useful, except some things can only be done with the elitebook laptop.  

Another nuisance issue is the ethernet port jumps to other subnet settings everytime the connection is lost (such as during reboot of device) and won't re-establish to same port settings without being told to.  (I suppose this problem will always exist)

---

### Post by yonnie on 2016-04-07
Could this be a browser problem?  Such as telling FF to login to 192.168.0.1 on one tab and telling it to login to 192.168.1.1 on another tab it gets confused and then won't connect to any port?

---

### Post by papibe on 2016-04-07
Hi yonnie.

Usually the network manager will try to establish a connection if the current one is lost. If you have wireless, and ethernet,  most certainly both connections are set to be 'Automatically connect to this network when it is available'. Thus. if you are rebooting a router in which your current connection is based on, you are producing the effect of 'where am I? I'll try to reconnect to whatever I found someone talking to me'.

I've been setting up a Banana PI as a router. Even if I was wired, when I rebooted the Banana, I would go back to my home wireless network... until the router come back successfully. What I did was set all my connections in 'Network Connections' to be _NOT_ automatic.

Now with this setup, after I reboot I just wait for a few seconds of lost connectivity, and then back to normal. In the worst case, I have to go and select my wired connection again.

Hope that helps. Let us know how it goes.
Regards.

---

