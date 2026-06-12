---
title: "Can ping router but not other pc's?"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by Jordy27 on 2008-10-05
I am trying to connect my linux pc to my windows network. However, 'network:///' shows a windows network icon but opening this does not show my network. 

I can connect to the internet fine (via wireless) and can ping my wireless router and adsl router fine (my wireless router is connected to my adsl router), however I cannot ping other pc's on the network, including my linux pc - I assume this is why I cannot see my other windows pcs?

On my windows laptop I can see other pcs etc fine, using wireless. Any help would be greatly appreciated!

---

### Post by Drezard on 2008-10-05
EDIT: Thought I'd add in a bit more information for people who people in future.

Windows XP and Vista pc's (If you have the SP2/3 firewall enabled) will block pings by default. So you may not be able to ping them.  

On the ubuntu pc type, 'ifconfig' in a terminal session and make sure all the information is correct. Check the IP Address is what it should be and the default gateway is your router. 

Back to the windows machines, make sure in the SP2/3 firewall has an exception for file and printer sharing. (Thats only if you want file and printer sharing, I'm assuming thats what you want to do. If it is something else, make an exception for that program/share) and then try and share those files again, make sure the directory has permissions of Everyone - Full access (This should give everyone who connects, read/write access to all files). 

Give those things a try and post results here if still not working.

Daniel

---

### Post by Jordy27 on 2008-10-05
Result of sudo ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:08:a1:b6:2e:eb  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17132 errors:0 dropped:116 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17924967 (17.0 MiB)  TX bytes:2252162 (2.1 MiB)

My default gateway should be 192.168.1.1 - I don't know how to find what this is set to? Firewalls should not be the problem - I can share files etc fine from my windows laptop.

Only other thing I just noticed is that the module Ipv6 (Internet Protocol Version 6) is blacklisted - I blacklisted it as part of a how to on setting up wireless but just wondering if this has anything to do with it?

---

### Post by Jordy27 on 2008-10-05
Hmmm just tried entering smb://192.168.1.2 in nautilus and it works! I can see my windows pc etc. However, using smb://studypc returns an error - Could this be because of a badly configured samba.conf? I would still like to know why I can't see other computers from network:/// but for now anyway I am happy just to be able to access files on my other pc :)

---

