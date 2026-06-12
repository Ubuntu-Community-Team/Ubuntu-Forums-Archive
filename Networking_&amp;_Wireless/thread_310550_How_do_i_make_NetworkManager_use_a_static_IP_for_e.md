---
title: "How do i make NetworkManager use a static IP for eth0 and dynamic for wlan0?"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by paulhollow on 2006-12-01
Hello...  Can anyone tell me how to get NetworkManager to use a static IP address for eth0 (my wired connection) and a dynamic address for wlan0 (my wireless card)?

The two interfaces are working fine, at the moment i am switching between them by using "sudo iface up/down" to disable one and use the other.  But it would be easier to use network manager.

When i comment out both interfaces in /etc/network/interfaces, NetworkManager picks up both interfaces ok, but tries to get a dynamic address for eth0 - this just ends up being garbage but seems to work ok for wlan0.

Is there any way i can tell NetworkManager that eth0 is static and wlan0 is dynamic???

Thanks for any help!

---

### Post by Tilex on 2006-12-01
If you go in your System Settings, under Network Settings, you should be able to configure eth0 and wlan0 seperately.  For wlan0, select automatic DHCP (or something like that), and for eth0, do not select DHCP, but rather specify your static IP, gateway IP (router's) and the subnet mask.

I would also be easier, in my opinion, if you configured your router to get static IP for only one of your two ethernet cards.  Each of them has an individual MAC address, so usually (for most of the routers), you can associate a static IP address with a MAC address.  Do so for only your "wired" card.  If you don't know the MAC address, type this in the shell: "ifconfig eth0", you should see something like "HWaddr:00:12:34:56:78:90"

---

### Post by paulhollow on 2006-12-03
Unfortunately, i want to use my laptop both at home and at work.  Work has the wireless network (using dhcp) and my home network is static.

If i try and configure the interfaces through system->admin->networking, i still have to use ifup/ifdown to manually bring the interfaces up and down again, depending where i am.  Network manager doesn't seem to want to do anything (it certainly doesn't show the nice gfx shown on the home page!) but will manage both eth0 and wlan0 if i comment them out in /etc/network/interfaces, but if i do that it then won't accept a static address and eth0 and sets it up with garbage data...

Surely, it must be possible to tell networkmanagaer that eth0 is a static IP address...???

Any ideas...?

---

### Post by spd106 on 2006-12-03
Sadly no, not at the moment. The best you can do is have network manager look after the wireless with wlan0 and set eth0 to be static in the network-admin gui as mentioned previously, i.e. comment out wlan0 only.

The only alternative would perhaps be to build n-m svn, not really recommended for a stable environment, unless you are very brave.

---

