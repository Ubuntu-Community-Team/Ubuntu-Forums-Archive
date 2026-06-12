---
title: "PCs don't &quot;see&quot; each other"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by trim17 on 2007-10-01
I have a desktop computer (home built) running Feisty 64-bit with two NICs. eth0 is connected to a router and gets its address via DHCP. eth1 is connected to a switch and is set up to have a static address of 192.168.0.1. The other computer is a Dell Inspiron 3800 running Damn Small Linux. It's connected to the switch as well. All connections are good (green lights). 

I have dnsmasq running as a DHCP server on the desktop. I want it to start serving addresses. But for some reason, the laptop won't "see" the DHCP broadcast. No matter how many times I try to get it to connect, it won't pick it up. If I set up a static address for the laptop, it doesn't respond to pings. I'm sure dnsmasq is running on the desktop, and set to only run on eth1. This problem has led to amazing frustration. What am I doing wrong?

---

### Post by MobiusNZ on 2007-10-01
Are both nics (on the desktop) set to different subnets? ie 192.168.0.1 and 192.168.1.1?

Can the lappy ping the desktop when its ip is set statically?

---

### Post by trim17 on 2007-10-01
I checked the subnets. Both are 192.168.0.x. Pinging with static addresses only results in host unreachable's either way (lappy to desktop, desktop to lappy).

---

### Post by MobiusNZ on 2007-10-01
That's most probably the problem. When you ping an address, how is the computer meant to know which network card to use? Different connected networks MUST have different subnets.
Try changing one network to 192.168.1.x and see how you get on.

---

### Post by MobiusNZ on 2007-10-01
Note that once you do get them talking, you'll need to set up the desktop as a router so that the laptop can access the net.

Seems to me like you're doing things the hard way. Plug the switch into the router, and both the desktop and the laptop into the switch, they'll get the dhcp from the router!

---

### Post by trim17 on 2007-10-02
The subnet for eth0 on the desktop is different from eth1, my local network card. The laptop's subnet is the same as the one on eth1 on the desktop.

I'm in a unique situation due to university rules. Only one MAC address can be registered to the ethernet port on my side of the room. So I can't test the NICs to see if they work from the router. That's also why I can't just plug the router straight into the switch. I know how easy it is to change your MAC address but I'd rather not have to hack this together.

I think I may have a faulty NIC/driver on eth1. I tried connecting eth0 to the lan. No luck, but when I pinged it from the laptop with a static address, Ubuntu showed that eth0(temporarily connected to the switch) was receiving packets but apparently not replying since the laptop reported 100% packet loss.. When I tried it again with eth1, no luck. It won't even receive any packets at all. I don't understand.

---

### Post by MobiusNZ on 2007-10-02
Maybe somethings up with your iptables, or as you say, with your nic? Or the switch?
Its a process of elimination - get the smallest possible amount working first and build up
Get a crossover cable and hook up eth0 on your desktop to your laptop would be a good place to start.

---

