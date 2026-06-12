---
title: "&quot;Network&quot; Feature - Need more oompf!"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by Aahz on 2010-05-30
Hello! I am a freshly baked Ubuntu user. So far, great ride. Managed to get Samba up, and, after 3 hours, even connect to it from my windows machine :-)

Now, to the question itself.

I live in a dorm, and we're trying to setup a local share between ourselves using the workgroups feature of windows. Our Network looks like this from my end:

My Windows Machine + my Ubuntu Machine -> Wireless d-link router(serves as DHCP to my two machines) -> residential gateway -> internet.

The d-link router gives out addresses to my two machines as follows: 192.168.0.1 and 192.168.0.2 . The router itself has to be manually configured and uses the adress 172.16.53.74 and connects to the gateway located at 172.16.53.254 . 

Now, I am the only one connected to the router, other people in the dorm just manually input adresses like 172.16.53.xxx and use the gateway at 172.16.53.254 to go online. When I go to their computer and click "network" we can see a few machines and we can connect two machines in the same workgroup just fine. 

However, neither my Ubuntu machine nor my windows machine detect any other computers other than the ones in my own subnetwork. In other words, the computers behind the router see each other just fine, but I cannot locate any computers that are on our dormitory network.

That is, I need my computer to be seen by other computers located behind 172.16.53.xxx IP adresses and I want them to see my Samba share on the Ubuntu machine. 

If it helps, the router is d-link MR814v2. I have disabled everything related to firewalls and such on the router, trying to make it as transparent as possible. But my computer knowledge ends here and I've hit a hard wall.

So, TL;DR: 

Ubuntu computer behind a router(acts as DHCP, assings 192.168.0.xxx adresses) needs to see the windows shares of other computers that connect to a residential gateway with an IP of 172.16.53.254 and the computers on that network need to see my Ubuntu Samba share.

If I can provide any more information, log files, configuration details, please let me know.

---

### Post by Ozymandias_117 on 2010-05-30
The only way I'm aware of to make this happen, would be to turn off DHCP and manually give them 172.16.53.xxx addresses.

---

### Post by Aahz on 2010-05-30
Right, I figured as much. So far, here is what I managed to pull off.

My router got a 172.16.53.74 external adress and 172.16.53.77 LAN adress. So, on my ubuntu machine I use 172.16.53.79 as my IP and 172.16.53.77 as the gateway. However, still no look seeing past the "residential gateway"(that is my router) in the "network" window.

---

### Post by marshmallow1304 on 2010-05-30
Try disabling the DHCP server on the router then plugging the connection from the gateway into a LAN port instead of the WAN port on the router.

Depending on the router, there may be other settings to change.  See [here]("http://forums.extremeoverclocking.com/showthread.php?t=188997") for possible suggestions.

---

### Post by Aahz on 2010-05-30
> **marshmallow1304 said:**
> Try disabling the DHCP server on the router then plugging the connection from the gateway into a LAN port instead of the WAN port on the router.

Depending on the router, there may be other settings to change.  See [here]("http://forums.extremeoverclocking.com/showthread.php?t=188997") for possible suggestions.

YOU ROCK WITH YOUR §$"( OUT!! Thank you! Been messing with this for hours now. Your solution worked brilliantly!

---

