---
title: "Need some help with routing tables"
date: 2005-09-22
forum: Networking &amp; Wireless
---

### Post by FishFoot on 2005-09-22
I have an ipw2200 WIFi Adapter and its giving me some trouble again.  I had been having some problems when I started but in the end the card just sort of started working.  All has been good up until now.

I installed openvpn (which kicks ass btw) while I was at a friends house on a wired connection.  When I got home I attempted to connect to my wifi network and failed.  I noticed that the tun0 interface was listed and that it had an IP address installed.  I checked the routing table and the vpn network was setup as my default gateway.  

Since I don't want openvpn to run when the machine boots I issued this command:

sudo update-rc.d openvpn remove -f

Next I attempted to bring up my eth1 wifi card and I got no dhcp lease.  For giggles I rebooted the machine (I know this isn't Windows) and when the machine came up I ran ifconfig and iwconfig.  iwconfig shows that the wifi card sees my router.  ifconfig shows an IP address leased to my card.

Here's the kicker... when I run route I see:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1

and then it hangs.  I have to ^c to get out of "route".  When I try to add the default gateway with a route command;
 sudo route add default gw 192.168.0.1 dev eth1
I get told that the route already exists.  

ARG!!!

Can somebody help me out.

Thanks
FishFoot

---

### Post by mlomker on 2005-09-22
> and then it hangs.  I have to ^c to get out of "route".  When I try to add the default gateway with a route command;
 

It's probably hanging trying to use DNS.  Use the **route -n** instead.

I'm not familiar with the command that you used to remove the init script. I suspect that **rmmod tun** would have worked for testing purposes.

---

### Post by FishFoot on 2005-09-22
Thanks for the reply mlonker.  Turns out wpasupplicant (which I setup for my work network) was running on startup.  I couldn't connect to my home network (which is open for the time being) because it was trying to use wpa and my authentication from work.

Thanks for the help
FishFoot

---

### Post by mlomker on 2005-09-22
[QUOTE=FishFoot]Thanks for the reply mlonker.  Turns out wpasupplicant (which I setup for my work network) was running on startup.  I couldn't connect to my home network (which is open for the time being) because it was trying to use wpa and my authentication from work.
[/QUOTE]

I actually gave up on wpa_supplicant after playing with it for a while.  I found the **whereami** package to be a better fit.

---

