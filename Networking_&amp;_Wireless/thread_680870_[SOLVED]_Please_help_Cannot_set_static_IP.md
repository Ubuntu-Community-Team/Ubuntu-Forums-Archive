---
title: "[SOLVED] Please help: Cannot set static IP"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by arbulus on 2008-01-28
Ok, so I'm having a fairly serious issue that has just materialized.

I'm running Ubuntu Gutsty 32bit with GNOME.

I've had a static IP address configured on my comp for a long time and have never had a problem until yesterday.  My ISP had an outage for about an hour.  I happened to be working on my wife's Mac at the time, so when the connection returned, I wanted to go back to my computer to make sure everything was good to go. Well, I couldn't get a network connection. I restarted networking, rebooted - nothing.  It wouldn't connect to the network.  So, out of curiosity, I opened up the Network manager (System>Admin>Network) and switched the connection back to DHCP, just to see if it would get an IP.  Sure enough, it connected right up. So, I switched it back to static but it lost the connection completely.  The most frustrating part is that I couldn't even connect to any of the other computers on my LAN - nothing at all. 

There's nothing wrong with my router.  Nothing has changed on my router, all my other machines are fine and functioning as they should be.  The static address was set on my computer and I want to keep it that way - I don't want to set an IP to MAC binding on my router.  I also do not want to use DHCP on this machine. 

Can anyone tell me what is going on here or how to resolve this?  Why would it just suddenly stop allowing me to use static IP addresses?  It's been working fine for quite some time.  Why on earth would it ever not work with static when it works fine with DHCP?  

Any help on this is greatly appreciated!

---

### Post by eteq on 2008-01-28
After you have the static IP set in the Network manager, try opening up a command line and typing "sudo ifup eth0" (or if your network card is named something other than eth0, put that name there instead).  If that doesn't work you might try "sudo ifdown eth0" followed by "sudo ifup eth0".

I had a similar problem, and this did it for me.

---

### Post by arbulus on 2008-01-28
The problem's actually solved now.  I'm really not sure what happened, but apparently the machine got confused as to which interface it was supposed to be using.  I don't use the onboard NIC, but rather installed a PCI NIC, and even though it worked before as I had it configured (as eth1) it now thinks it should be eth0.  After restarting networking, disabling eth1 and rebooting, it seems to be working fine now. 

It's really odd how that happens.  I actually had something similar happen to me a while back with an external HDD.  When I first ever plugged it in, it was /dev/sde.  But for some reason, a few weeks later, Ubuntu decided to change it and made it /dev/sda completely without my knowledge or consent. 

Thanks for your suggestion, eteq!

---

