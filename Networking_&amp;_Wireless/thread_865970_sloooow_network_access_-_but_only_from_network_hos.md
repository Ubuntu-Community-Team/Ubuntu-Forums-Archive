---
title: "sloooow network access - but only from network host"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2008-07-21
Hi All.

I've got a mixed home network at my flat, and a few of the network nodes are mine - three computers at the mo, and a bunch of handsets.

Anyway, my Hardy desktop has slow connectivity, and I don't have a clue as to why.
Another machine in my room, a hardy laptop gets normal speeds. So does my mac and my handset.

I restarted the network a couple of times from the init script, but that did no good. Still sloooow. Google takes about a minute and a half to load.
The desktop machine is acting as if there is network congestion, when in fact there is none.

I fired up wireshark, and I could see that the router is responding as it should. (From what I can work out).
But, there seems to be significant delay between in the response time from the desktop's wireless interface.

Otherwise, the machine is fine. In every other way it is perfectly responsive. It's only slow in regard to the network.

Dropping the firewall on the machine (dropping all iptables rules and setting default policy to accept) doesn't alter this behaviour.

What could be happening here?

- some factors that could be influential...
I have vmware installed. On boot, vmware adds two interfaces, vmnet1 and vmnet8 that I have to take down with ifconfig if I want any networking at all to work. This has become routine for me, and hasn't seemed to effect network speed before.

This is a serious problem for me, (ie, I'm missing out on reddit.com!), so
I'd most appreciative of any help.

Thanks

---

### Post by bobdobbs on 2008-07-21
update - 

More wierdness.
The wireless interface spontaneously vanished.

Then reappeared.

Now the speed is back to normal.

I'm guessing that it might actually be the wireless network adapter...

---

