---
title: "VMNetwork with Complex Bridging?"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by shaddie on 2008-07-19
Hello ^_^

I just had some questions about how linux TAP devices work. I've been trying for about four days to get things working with a linuxy KVM approach rather than Xen. No luck so far ;(. I've followed like 20 different guides, but none seem to do what I want.


KVM seems to use all TAP devices - which I thought would work. Unfortunately they work far differently than how I originally thought.  I need virtual machines to be members of different software bridges.

In short, what type of device will function strictly as a virtual nic connected ONLY to the bridge it is in?

Below is kind of what I wanted to do.
___________________________________

Internet (eth0)
|
External Switch - VM Firewall External NIC


Internal Switch - VM Firewall Internal NIC  
|
Internal Hosts


I want the VM to handle the traffic passing from external to internal.  The idea is to be able to swap out different OS'es at the firewall spot to easily see the strengths/configuration differences.

I created the different software bridges and tap devices using brctl and tunctl.  Unfortunately, tap devices are more like copies of eth0.  They seem to always have access to eth0's ethernet. 

What type of device will function strictly as a virtual interface? It should only have access to the ethernet of the bridge that it is in.



:)

---

