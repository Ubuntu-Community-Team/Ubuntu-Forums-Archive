---
title: "Have to reset router to get connection"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by benkomalo on 2005-08-07
Hello folks, 

I've searched through old posts and google, but this is sort of an odd problem so I haven't had any luck. Was hoping someone could help.

I recently installed Ubuntu, and couldn't get my net connection to work properly. If I reset my router, I get connection and everything works fine.  However, everytime I restart Ubuntu the problem reappears and I have to reset my router to get connection again.  This is quite annoying. 

Any help would be appreciated,
Ben

---

### Post by spanishwasabi on 2005-08-07
Hi,

Just guessing... do you use a DHCP server?

Maybe what happens is that your computer gets with DHCP an IP address when you reboot the router...

Does it work with Windows?

You should tell a bit more about the kind of network you're using, the steps you follow to connect to your network...

Try this:
sudo dhclient eth0
(eth0 or whatever the name of your interface).

G

---

### Post by mrcbrown on 2005-08-07
Did you hardcode a IP? If your router does DHCP and you have hard coded your linux rig with a IP it may be fighting for who get's it on the router - thats definately another possiblity - but do tell more about your config - also model of router as well.

---

### Post by benkomalo on 2005-08-07
Hi again,

Thanks so much for replying. I'll try my best to describe my setup:

I have an SMC router. There are 3 machines on it, of which one is mine. I have a dual boot WinXP/Ubuntu.  

I believe I am using DHCP, though to be honest I'm a networking noob so I'm not 100% sure. I haven't had to specify an IP in linux or windows before so I'm presuming it does use DHCP.

I have MAC filtering set up, however, and I'm not sure if that automatically assigns the same IP for each MAC address. I seem to be getting 192.168.2.101 most (all?) of the time.  My windows partition works fine with the network, except for when I boot into Ubuntu and "break the connection."  Once the connection is broken from a boot into Ubuntu, rebooting into Windows does not fix the problem - I have to reset the router.  However, once it's "fixed", I can restart in windows however many times I please and connection will still be established. 

I tried the dhclient eth0 command, not knowing what it does in the slightest. The response is:

[FONT=Courier New]Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:00:21:01:3d:94
Sending on   LPF/eth0/00:00:21:01:3d:94
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.101 -- renewal in 259305 seconds.[/FONT]

Again, thanks so much for the help.  I have always been amazed at communities like this where people are willing to lend a hand in return for mere thank you's.

If there is something I have missed, please let me know

Ben

---

### Post by mrcbrown on 2005-08-11
[QUOTE=benkomalo]Hi again,

Thanks so much for replying. I'll try my best to describe my setup:

I have an SMC router. There are 3 machines on it, of which one is mine. I have a dual boot WinXP/Ubuntu.  

I believe I am using DHCP, though to be honest I'm a networking noob so I'm not 100% sure. I haven't had to specify an IP in linux or windows before so I'm presuming it does use DHCP.

I have MAC filtering set up, however, and I'm not sure if that automatically assigns the same IP for each MAC address. I seem to be getting 192.168.2.101 most (all?) of the time.  My windows partition works fine with the network, except for when I boot into Ubuntu and "break the connection."  Once the connection is broken from a boot into Ubuntu, rebooting into Windows does not fix the problem - I have to reset the router.  However, once it's "fixed", I can restart in windows however many times I please and connection will still be established. 

I tried the dhclient eth0 command, not knowing what it does in the slightest. The response is:

[FONT=Courier New]Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:00:21:01:3d:94
Sending on   LPF/eth0/00:00:21:01:3d:94
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.101 -- renewal in 259305 seconds.[/FONT]

Again, thanks so much for the help.  I have always been amazed at communities like this where people are willing to lend a hand in return for mere thank you's.

If there is something I have missed, please let me know

Ben[/QUOTE]
 Almost seems like it may be a issue with your router not liking the hardware name change using DHCP - some router DHCP servers cache computer name & such, so it may be just getting confused and a reboot of it clears the cache and it works again.

I personally haven't dual booted in years so I can't speak of any recent experiences with routers, but maybe try shutting off Mac filtering for giggles and see if that helps.

---

### Post by sqdtnz on 2006-11-22
Hey there,

I have a VERY similar problem:

I have a router too, 3 pc's are connected to it:

- Windows XP upstairs
- WhiteBox Linux upstairs
- Ubuntu  Linux downstairs

Downstairs I used to have WhiteBox aswell, but I changed to Ubuntu because it's so much easier to find and install proper software for it, in my opinion.

There was never a problem with Whitebox on that PC in the past, but whenever I start up the Ubuntu computer my internet goes crazy, with the following symptons:

- all URL's with domain names stop working (DNS?)
- IP's to those websites DO work, so when someone told me the IP to the Google site, it did work.
- When I reset my router internet worked normally again on every PC.
- The domain/ip problem occurs **on every PC**, also on my Windows I can't access domain names anymore. So Ubuntu somehow changes the entire network, it must do something to my router.

I'm not in the mood to constantly reset my router when I turn on that computer, so any suggestions will be really welcome!

Greetings,
Paul

---

### Post by stream303 on 2006-11-23
Ah, pinging and dns issues.  Something I just wrote might help:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

