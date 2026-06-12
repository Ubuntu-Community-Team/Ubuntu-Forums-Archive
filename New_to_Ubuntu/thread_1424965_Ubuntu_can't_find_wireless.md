---
title: "Ubuntu can't find wireless"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by obi42 on 2010-03-08
Hi,
 
I have come across a weird problem and I'm relatively new to Ubuntu, so I'm at a loss.
 
I have just moved into a new apartment building, and I had to purchase a new wireless router as the old one was incompatible with the cable service provided in the apartment.
I bought a D-Link DIR-600, which seemed sufficient for my needs.
 
Now, my Windows laptop (HP Elitebook) has no problems finding and connecting to the router. Neither does my Nintendo Wii, for that matter.
But my Ubuntu laptop (Dell XPS 1530, Karmic) refuses to acknowledge the existence of my router. It has no problems detecting up to 10-15 other wireless networks in adjoining apartments, and it can even connect to a couple of unprotected ones ;) but my own router remains invisible.
The laptop worked fine with the old router in my old apartment.
 
I have no clue what to do, as it seems like every component is working fine - just not together. 
 
Help!

---

### Post by MichealH on 2010-03-08
Does your router have a hidden network on it by Default? Have you even set one up?!?

---

### Post by kitschl on 2010-03-08
You could try adding your network manually. Go to System>Preferences>Network Connections, go to the Wireless tab, then click on Add.

[LIST]
[*]In "Connection Name", you can put whatever you want. 
[*]Check "Connect Automatically". 
[*]In the Wireless tab, enter the SSID of your network. Make sure "Mode" is set to "Infrastructure". 
[*]In the Wireless Security tab, change settings to match the security you set up on your router. 
[*]In the IPv4 Settings tab, change settings to match your router's configuration; if you're using DHCP, just set "Method" to "Automatic (DHCP)", and that's all.
[/LIST]

I assume since your Elitebook and Wii are able to find your router, your network isn't hidden; and I assume that your Ubuntu PC's wireless is configured correctly, since it is able to find other wireless networks in your building. 

Another thing you might consider: If your wireless network begins with a letter far down in the alphabet, like 'v', and there are many other wireless networks in your vicinity, perhaps your network is too far down on the list to be shown. May or may not be accurate, but it is something that I have seen before. 

Please let me know whether this helps you. Good luck!

---

### Post by obi42 on 2010-03-08
I have tried adding the network manually, but that didn't work either. :(

The network starts with an "a", so it should easily show up on the list...

---

### Post by kitschl on 2010-03-08
That is odd. Other wireless networks show up, but not your own... 

You've probably already tried disabling/re-enabling your laptop's wireless card, and power-cycling your router...

You could try making sure that you have updated your router to the latest official firmware, sometimes outdated firmware can cause issues with interfacing. The same for your wireless card drivers. 

The only other thing I can think of is to check that your router is broadcasting a signal that your Ubuntu laptop can recognize; maybe you are broadcasting in 802.11b, and your laptop can only recognize g.  

I hope this helps.

---

### Post by obi42 on 2010-03-08
That did the trick! I changed the routers signal from 802.11n to 802.11b and that worked. I would never have worked that out by myself, so thank you very much! :D

---

### Post by kitschl on 2010-03-08
That's great! I'm glad I could help. :)

---

