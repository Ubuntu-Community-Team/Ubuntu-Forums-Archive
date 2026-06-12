---
title: "[SOLVED] Network Bridging in 8.10"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by thon0925 on 2008-10-04
I have freshly installed Ubuntu 8.10 beta on my Dell desktop. It has a Netgear WG311V3 network adapter with ndiswrapper and a wired connection that is built into the motherboard. I have this computer setup in my living room and I would like to bridge the wireless to the wired connection, so I can have my older game consoles to connect via the wired internet. The wired connection is plugged into a network hub that is connected to my older consoles. The new network manager has some new options such as allowing a connection to be shard to other computers, but I cant seem to get the connections to bridge.
any ideas?

---

### Post by thon0925 on 2008-10-04
I was able to resolve this issue with Firestarter.
For anyone else with this problem, use the network manager to specify a manual IP address for your wired connection.(I used 192.168.1.1) 
NOTE: You must either have a crossover cable, network hub or network switch for this to work.
Then make sure both the wired and wireless connections are active.
Then install Firestarter
```
sudo apt-get install firestarter
```
then configure your setup with the wizard that comes up when you launch Firestarter. Enable internet connection sharing and DHCP.
NOTE: you must have dhcp3-server installed
```
sudo apt-get install dhcp3-server
```
After this you should be able to connect to the internet automatically from the network hub. Happy networking :)

---

### Post by cashman04 on 2009-01-04
Thanks for this guide.  It seems a lot better than doing it any other way.


> **thon0925 said:**
> I was able to resolve this issue with Firestarter.
For anyone else with this problem, use the network manager to specify a manual IP address for your wired connection.(I used 192.168.1.1) 


One thing though, this is the only part i don't know how to do.  You think it would be the simplest.  I think it is cause on 8.04 you can manually put in the ip at the network manager.  But under 8.10 I don't see anywhere that will allow you to do that.

Any one have any ideas?

---

### Post by thon0925 on 2009-01-04
You should be able to right click on the network manager and hit "edit connections". From there you should be able to go to your wired connection and edit it to have a manual IP address. Just make sure your wireless connection has a different IP address than your wired connection. (for example, Wireless - 192.168.1.2, Wired - 192.168.2.2)

---

### Post by cashman04 on 2009-01-04
I can do that on 8.04, but under 8.10 I have to go down to Configure vpn.  Then click on the ethernet tab.  From there I can change mac address and a lot of other stuff, but no the ip, dns, and gateway.

Either I'm blind or really dumb, cause I couldnt get it to work all last night.  The only way i could even get the eth0 to connect to anything was to plug it into one of the outgoing plugs on my router.  I tried plugging it into the internet plug, my macbook, and even my xbox 360.  When i clicked it, it wouldnt connect to any of them, and therefor I couldnt start the firewall, because it was disconnected.

I'll try some more tonight, but if i dont find anything, I'm going back to 8.04.

Still, thanks alot for posting the firestarter program, this will end up making it alot easier to share connection.

---

