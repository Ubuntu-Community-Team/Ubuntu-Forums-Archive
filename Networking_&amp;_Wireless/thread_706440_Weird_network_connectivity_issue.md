---
title: "Weird network connectivity issue"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by AndyNJ on 2008-02-24
I've done a lot of googling and searching this site and nothing that i've found seems to help. 

I'm running Gutsy on my laptop and can't get a working connection to my network. Here's the situation, maybe someone knows what I can do:

- everything was working fine and then i went out for a few hours and came back to this (no reboot was involved)
- no difference for wired or wireless
- every other computer on my network is fine and if i boot into windows or a linux live CD, i have no problems
- computer gets an IP address from my router (DHCP) and says that it's connected, but my router doesn't show it as connected and i can't connect to anything on my network or the internet
- i can ping the router fine, but i can't ping anything else on the network
- no other computer on the network can ping this one
- i've tried rebooting multiple times since
- i've reset the router and the cable modem 
- if i try to connect to my neighbors' unsecured wireless networks, i get the same problem

help!

---

### Post by AndyNJ on 2008-02-24
A little more information...

The last thing that I had done before things stopped working was install VMWare server and it seemed to have created vmnet1 and vmnet8 as network devices. This didn't seem to cause any problems right away as things were still working, but maybe it's possible that my wireless connection had dropped for a second and then when it reconnected, the problem arose? Unfortunately, since the problem seemed to go down sometime when I wasn't actually on my computer, I have no idea.

---

### Post by AndyNJ on 2008-02-24
Diving into this further, vmnet1 has an IP address of 192.168.1.1 listed. That's the same as my router. After tracing the ping request to this IP, I've realized that i've been pinging this instead of my router. 

So it looks like there's and IP conflict between vmnet1 and my router that is causing this. However, I can't figure out how to edit this network device's properties/settings. 

Or even better, how can i remove this device?

Anyone know?

---

