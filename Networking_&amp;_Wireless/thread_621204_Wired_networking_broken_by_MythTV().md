---
title: "Wired networking broken by MythTV(?)"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by JimBobble on 2007-11-23
First, please forgive the long explanation.  I have been running Gusty for a couple of weeks now with little trouble, but I am largely a rookie.  My machine has two network interfaces, eth0 and eth1, both of which worked fine before today.  I also have a WinXP virtual machine which is also able to connect fine (I'm in it now).

Now for the meat of the problem:  I installed MythTV via Synaptic and configured it in the usual fashion.  After doing that:
[LIST]
[*]I CANNOT connect to the internet or local network shares from Gutsy.  
[*]I CAN ping my router and other machines on the network from Gutsy.
[*]I CAN access the internet and the network from inside the WinXP VM.
[*]I CANNOT do an NSLOOKUP from Gutsy (server does not respond), but I CAN from WinXP VM.
[/LIST]

Here are some other facts, in case they are helpful:
[LIST]
[*]I usually run on eth1; I switched to eth0 by moving the cable and it doesn't work in Gutsy either.  
[*]I tried changing ports on the router for grins, with no change.
[*]I tried changing IP addresses by manually configuring one in Network Settings; it didn't help, either.  I went back to "roaming mode."
[*]I removed as much of MythTV's installation as I could find using Synaptic; no help.  It originally installed 45 packages and I have only removed 15 or so, so there's obviously more there that I'm missing
[*]I do not appear to have iptables or Firestarter installed
[*]I tried ifdown and ifup in the terminal; they reported that eth1 was an unknown interface
[*]I rebooted the router, again just for fun, with no change
[/LIST]

I guess that's about it.  I'm sure it's probably an easy change somewhere, but I'm at a complete loss.  It confounds me that I can do whatever I want from a VM inside of Gutsy, but Gutsy itself can't do anything.  What am I missing?

---

### Post by JimBobble on 2007-11-23
I should also mention that DHCP seems to be working properly; I have the same IP address that I've had throughout.

Thanks in advance for the help!

---

