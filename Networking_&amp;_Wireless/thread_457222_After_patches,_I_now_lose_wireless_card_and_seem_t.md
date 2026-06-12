---
title: "After patches, I now lose wireless card and seem to have to reboot"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by rickcr on 2007-05-28
Hopefully I'll describe the situation correctly. Just recently (about 4 or 5 days ago I applied some updates through the update manager). Now, for some reason I'll wake up in the morning and I won't be able to connect to my router at all. The wireless card shows up in the network tools and I've tried disabling it from there and enabling it again, but still no luck. What is odd is I can't even connect to the router admin address (192.168.2.1) it's as if the card isn't even working. However, if I reboot the computer things will work fine, and they seem to stay fine all day and into the evening (at some point during the wee hours of the night, something goes wrong.)

If it matters there were a few things in the past I had done (but haven't had any problems until the last batch of updates)... I had to download my driver for the card and used ndiswrapper to install it. I also have my network setup where the machine is given a static IP. My config looks like..

ip: 192.168.2.11
sunet mask: 255.255.255.0
gateway address: 192.168.2.1

dns server tab I have: 192.168.2.1

I also have dynamic DNS setup on my router using the DynDNS provider. 

Again, though, all of this was working flawlessly for a while now. It's only recently that I'm having the issue where I need to reboot to get things working again (obviously I understand it's linux and there is probably some init.d script I could rerun instead of rebooting, but I'm a newb here.)

Thanks for any help.

---

