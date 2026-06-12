---
title: "No connection in Package Manager, but works in Firefox"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by sipickles on 2007-11-05
Man, ubuntu networking is terrible!

I've spent days sorting my laptop's wireless (now works!), only to find my desktop is even worse, despite a dhcp wired connection. I mean, how elementary is that?

So my desktop finally has internet thru firefox, but not with package manager. 

I've done all the alias mods, and black listed ipv6. ifconfig gives me:

eth0      Link encap:Ethernet  HWaddr 00:C0:49:63:58:83  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2321255 (2.2 MB)  TX bytes:449533 (438.9 KB)
          Interrupt:11 Base address:0x8000 


So it says its working.... wtf is wrong with synaptics?

Help, before I reboot to windows XP!!!!

:)

Si



---- weird. I can ping ubuntu.com but not archive.ubuntu.com. Does that mean its not me? can anyone test this for me?

---

### Post by sipickles on 2007-11-06
<bump>

Still struggling on this one.....

---

### Post by NIT006.5 on 2007-11-06
If it works for one thing and not the other, it doesn't sound like it's a networking issue. More likely a config issue somewhere. How are you connecting through firefox? Do you use a proxy or direct?

---

### Post by spd106 on 2007-11-06
Which repositories are you using? Check in Software Sources.
 
If you're on a local one, try changing to the main repos or another local mirror.

Also try using apt-get from a terminal, just in case Synaptic is at fault.

---

