---
title: "VERY weird problem."
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by MyBrainReallyHurts on 2008-07-21
I recently installed Ubuntu on my Windows XP laptop using Wubi. 

Ubuntu 8.04

Whenever I connect the laptop to the network and boot to Ubuntu, it kills my network. Everything slows down and eventually I have to restart my router and firewall (Sonicwall)

Today, I tried to do something totally different. I configured the wireless via Ubuntu and connected to a wireless router OUTSIDE of my network. 

Here is the really weird part...I still lose my network connection within the network. 

WTF?

My theory was that Ubuntu was creating some sort of broadcast storm, and that was the reason why it was causing a problem while connected to the network. Now that I am connected outside the network, I am completely confused. The laptop is not on the network at all, and the router and firewall have no wireless capabilites. 

Yes, I tried it twice with the same result. When I boot up into Windows, I do not get this problem. 

Does Ubuntu have broadcasting enabled by default? Does the Wubi setup create some sort of loop? 

Any and all ideas will be appreciated with this weird one.

---

### Post by SpaceTeddy on 2008-07-21
mhm - this is interesting...

The only reason i could possibly think of is that you created a loop in your local network, thus flooding it with arp queries. But for that, you'd need to bridge at least two network devices together on the ubuntu machine and plug them both into the same network. 

The only other possible reason i could think of is that something in the networking is wrong. But i have never seen a linux (no matter if ubuntu or something else) crash an entire network just by being plugged in.
Do you have any other hardware installed on the machine ?

One last question - how is your network configured ? via dhcp ? or static ip ?

hope we can figure this out... somehow (i really don't have many ideas myself)

---

### Post by MyBrainReallyHurts on 2008-07-21
DSL Modem - Sonicwall Firewall - all workstations plugged into the Sonicwall. 

Windows XP on the laptop. Ubuntu installed via Wubi. 

Only the basic hardware is in the laptop. Built in wireless and nic cards. 

The Sonicwall is responsible for the DHCP, although I have given each workstation an IP address manually within the IP range. (Static)

When the laptop is plugged into the network via Windows, it works perfectly. 

When the same laptop is plugged into the network via Ubuntu, everything works perfectly...for about ten minutes, and then I lose my connection. I remove the laptop from the network, restart the firewall, and then everything is happy again.

The weirdest part is how the laptop, when connected to an open wireless signal I find outside the office, jams up the network inside the office.....freaky.

---

