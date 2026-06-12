---
title: "Network keeps going up and down ,offline"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by mdcatc on 2008-07-17
I'm running an Ubuntu Server 7.10 and I have two network cards on the box. eth0 is configured as static and exposed as my WAN side. and eth2 is configured as static and exposed as my LAN side.

The eth0 keeps going offline, an ifconfig shows everything as normal.

I've been running a PING from a second external machine to monitor the availability of the machine and it will go from being available to unavailable and then without any change, goes back online.

The status line from ifconfig shows the same when working and when not working:
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

If my PING's arn't getting thru and I execute /etc/init.d/network restart things return to a working state. This tells me its definitely something on the machine itself and not something from my ISP's router etc.

I'm not sure what log file I should be looking in to identify what may be causing this behavior. 

Is there a setting on the network stack somewhere which would deactivate the interface if idle for any amount of time?

I guess its possible to have a bad card.

Any suggestions would be helpful.

LunarDraco

---

### Post by schmildo on 2008-07-17
The first thing i'd try is swapping the cards over. Swap the IP's and cables around.
  That way even if nothing different occurs; You've wittled the problem down a little.

What is the externally facing card plugged into?

---

### Post by mdcatc on 2008-07-18
The external (eth0) facing card is a PCI card. Not sure on the brand or chipset.
The internal (eth2) facing port is on the motherboard.
I'll switch the network configs/cables on the ports later today and monitor them for a while to see if the symptom stays with the card or if it stays with the configuration.

LunarDraco

---

### Post by mdcatc on 2008-07-23
ok, I've put a new network card in and configured the IP on interface eth3.
And still having the same symptom. 

Something software is disabling or blocking the interface.

I have blockhost installed and configured and it is working as expected. I've disabled blockhost for a period of time, and the symptom continues to occur.

Does anyone have any ideas as to where I could look in logs etc. What I might look for? Anything I could check with ifconfig. Isn't there another command that gives better results for the network, including hardware status etc.

---

### Post by rafaelmagu on 2009-09-10
I've been experiencing the same thing. But in my case, Ubuntu is installed in a virtual machine with a virtual network adapter. The host is responsive while Ubuntu just ceases to respond on the network.

Don't know what is causing it, but I'm sure it's not hardware. (Other VMs on similar hosts work fine.)

---

