---
title: "How to set up a static IP address in Ubuntu Fiesty?"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Goombie on 2007-06-23
Ok, I have two questions here:
I have a couple programs (Bittorrent and a game) that I have port forwarded on my router, but for them to work correctly, I also need to set up a static IP address in Ubuntu, and I don't know how to do that. Anybody have any ideas?

Also, I've been using the default network-manager-gnome applet for managing my internet connection, but I was wondering if there was any better programs out there. I tried Wicd, but that just broke everything. :(

Thanks in advance!
:popcorn:

---

### Post by jimrz on 2007-06-23
> **Goombie said:**
> Ok, I have two questions here:
I have a couple programs (Bittorrent and a game) that I have port forwarded on my router, but for them to work correctly, I also need to set up a static IP address in Ubuntu, and I don't know how to do that. Anybody have any ideas?

Also, I've been using the default network-manager-gnome applet for managing my internet connection, but I was wondering if there was any better programs out there. I tried Wicd, but that just broke everything. :(

Thanks in advance!
:popcorn:

1- simplest way is to go into your router and look for a place, on my netgear it is call "LAN IP Setup", that allows you to reserve a specific IP, by comp name/mac address, for specific boxes and set what you need. this will give you "static ip" functionality while still allowing you to leave ubuntu set to dhcp and keep network-manager. additionally, in the case of a laptop you need not worry about adjusting your settings when using other than your own network, as it will already be dhcp. this is also handy for things like ssh, which i prefer over and use much more than samba, as it seems that specifying a target by ip addy is much less hassle and works better than doing so by name resolution.

2- i like the default, so have not tried the other options none of which seem to offer any major improvement. the 2 things i don't like are 1- no good way to get static ip setup in NM itself (see work around above) and 2- it does not seem to see any AP that does not broadcast it's essid. hopefully the devs are working on both.

---

### Post by Darganot on 2007-06-23
I have a static ip set up but doing what the above poster recommends isn't enough for me.  I need to go into system > administration > network (location in kubuntu varies) and use the native networking tool.  Click on wired connection then properties, then change from dchp to static.  Remember to set your ip like you did in your router's software.  Then set your subnet mask and gateway address (hopefully you know those, the second is the ip you put into your browser to dial into your router, the first is usually 255.255.255.0).  Close this then don't forget to click the DNS tab and enter your domain.  Hit ok, and you might need to restart but it should work.

---

### Post by Goombie on 2007-06-24
Jimrz, do you know if I can do that with Linksys routers? I have a Linksys WRT54G.

Thanks for that info Darganot, but I should've mentioned that I'm on a wireless network. :)
Does changing the wired connection to static IP work for the wireless connection as well? I'm a little confused as to how that works, or if I can do it from my router instead. 

That's one thing I could do easily on Windows - setup static IP addresses.

---

### Post by jimrz on 2007-06-24
> **Goombie said:**
> Jimrz, do you know if I can do that with Linksys routers? I have a Linksys WRT54G.

Thanks for that info Darganot, but I should've mentioned that I'm on a wireless network. :)
Does changing the wired connection to static IP work for the wireless connection as well? I'm a little confused as to how that works, or if I can do it from my router instead. 

That's one thing I could do easily on Windows - setup static IP addresses.

almost certain that your linksys will do that, most current routers will. just type the router's ip address into your browser, enter it's setup and look for something like LAN IP settings. i seem to remember that linksys uses 192.168.1.1 for the default router address but not certain, you can check in your manual or their website.

---

