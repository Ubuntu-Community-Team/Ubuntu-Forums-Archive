---
title: "[SOLVED] Static IP for Mythbuntu backend"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by yonkiman on 2008-08-03
I've got a typical home network with a wired/wireless router (Linksys WRT54G) connected to my cablemodem.  One of the wired ports runs across the house to a 5-port switch (Linksys EZXS55W).  One of the switch's ports goes to the new Mythbuntu machine I just built.  Everything in my house has been DHCP until now, which has been fine, but now I'd like to fix the IP address of the Myth box so I can guarantee it will not change with reboots (of the PC/router/switch) or if for some reason the ports get switched on the router/switch.  (This is because Myth frontends look only for an IP address, not a computer name.)

This is probably trivial, but I barely understand any of this networking stuff.  Setting a static IP address in Ubuntu's Network settings (and hoping my router/switch somehow connects to it) doesn't seem to work.

I also don't understand exactly how the switch works - does it get one IP address from the router (since it's only using one router port) and expand it into 5 IP addresses, or does the router assign 5 IP addresses that it switches between at the switch level?  I looked for a FAQ I could comprehend but couldn't find one.  

And what's the difference between DHCP and "Enable Roaming Mode"?  When I started all this, Ubuntu seemed to have defaulted to "Roaming Mode", and everything worked OK.  But after trying static IP, "Roaming Mode" no longer worked - I had to select DHCP.  Not a problem, just curious...

My goal is for all the computers on my home network to see this one PC at an unchanging IP address.

---

### Post by eldragon on 2008-08-03
the switch does nothing at all, it doesnt get an ip assigned. even the router at its 4 LAN ports has a switch itself.
the router behaves as the following.
a NAT
a switch
a DHCP server

the router's dhcp server usually assings ips to computers requesting for them in a predefined range, for a linksys router this will be between the 100 and 200 range (say 192.168.1.100~200).

if you tell your computer to have a static ip (make sure you assign an ip that doesnt belong to the dhcp range), say 192.168.1.11. it will not hunt for a dhcp and ask for an ip there.

next thing, you need to tell your computer which is the router's ip, in this example, it would probably be 192.168.1.1. then the router makes all the magic.

the switches only behave as relay points between computers.

i hope ive been clear enough.

good luck.

---

### Post by yonkiman on 2008-08-03
That worked!  The odd thing is that that is exactly what I tried doing before I posted - I'm not sure what changed...

Thanks for the super-fast answer and background info!

---

### Post by mythbuntu101 on 2010-01-20
I can't get it to work. What do I need to do? Can you tell me how to do it in Mythbuntu? Do I need to update the router?

---

