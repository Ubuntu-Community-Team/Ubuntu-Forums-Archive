---
title: "Dial on demand, mc"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Aleksanderx on 2007-01-13
I've just installed 6.06 server (no X) and need to make some config changes.

Story (skip if you don't care what we're doing)
This is going to be a demo of how easily linux handles dial on demand routing, since the box is used to connect to several dozen remote machines we have logging data for our process control systems. We are having significant trouble getting Windows 2003 to do this, though it is documented that it can. I want to kill Windows from this special box, and now is my chance to convince the boss. The machine will be running apache2.2 and mysql5 and webusers will be forcing the DOD up when they want real-time data. Very cool stuff. I used linux for a couple years a few years ago, so I'm familiar but not an expert.
End of story

First, I desperately need midnight commander (darn you Ubuntu weirdos: who ever heard of a server without mc? no offense, eh, to each their own!). aptitude and apt-get don't list mc, and even if they did, would not be able to install it, since I can't find the nameserver settings, which are certainly wrong. As a workaround, I am manually ifconfig'ing eth0 to be on the same net as my router, making the router the gw, but still need to tell ubuntu which namesevers to use at my ISP. **Where is this setting, and what other changes must I make to apt-get mc**?

Next, I need to configure DOD to dial on demand 192.168.3.1 at phone number 123 4567 and correctly set up the routing table. We have dozens of such remote machines, and therefore dozens of DOD routes to set up. **Where can I find DOD guidance?**

The box is 192.168.1.1. Our ADSL router is 192.168.0.102 (note the different net). Our nameservers are at the ISP.

In the name of eliminating Windoze, I thank you for reading this.

Sincerely,
Aleksander

---

