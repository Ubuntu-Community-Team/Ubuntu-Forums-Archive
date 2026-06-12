---
title: "multiple network configs"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by knichel on 2007-08-03
I have a laptop and I often connect to different networks.  I have a wireless network at home with its own ssid and wep key.  I have one at work with a different ssid and wep key and yet another at my mothers house.  When at work, I also use a wired connection to get to an internal network.  I also do wireless broadband installs for a local isp and need to be able to connect to the service unit with a wire using pppoe to connect.  The service units come with a 192.168.100.100 as a default ip address and we change to 10.x.x.x address.  So, how can I create different network settings effectively.  I have not had  any  luck using profiles.  BTW I use kubuntu.

On a windows computer it is possible to assign several ip addresses and netmasks to the wired port.  Can this be done with ubuntu?

Is there a good network switching program so I can easily switch my wireless network and have all my settings change as needed?

Thanks in advance for any help,
Mike

---

### Post by cmnorton on 2007-08-26
I keep a wired ethernet connection enabled, when I go to work and plug in an ethernet cable, regardless of whether or not I pull the wireless modem card -- also set up with ssid and web -- I have connectivity.

I am not quite sure what Locations (Profiles) provide. I know what they are supposed to do, obviously, but there are certain nuances in how they behave. Having one interface and using the icons in it, eth1 wireless at home and eth0 for work, works for me.

---

### Post by knichel on 2007-08-26
Thanks for the tip.  That would be fine except I use several different wireless networks.  I need to find a way to switch wireless networks (and settings) without reconfiguring the adapter each time.

Mike

---

### Post by timmahhny on 2007-08-27
I am attempting the same thing as I write this.
I need at least four wireless connections.
If you find the answer, please post here.
thanks
Timmahhny

---

