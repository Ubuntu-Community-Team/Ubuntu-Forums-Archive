---
title: "IP Cop Using Computer as a router"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by arphe_el on 2006-11-21
I'm planning to use IP Cop if you're familiar with this software and using a computer to function as a router that will connect to the network.

Any suggestion as to how can i configure it the hardware set-up?

Does anyone familiar with this set-up?

---

### Post by Jimmey on 2006-11-21
That'll depend on what you're trying to do.

I have a machine (my laptop) that acts as a router. Here are some thing you'll need to know:

You need to configure two seperate network interfaces. One of these interfaces will be the one which connects to the internet (either directly, or through another router); the other interface will be the one connecting to the other computer on the network. 

You'll need to make sure that the IP's are different for the two interfaces. If one interface's IP is 192.168.1.199, then the other's must be something like 192.168.0.2...Well, you get what I mean.

For the machine connected to the router computer, it's important that you set a DNS address that's identicle to the one you use on the router.

With a bit more information on what you want your network to be like, I can probably help you out more :-P

---

