---
title: "What is the &quot;sudo route add&quot; command for this?"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by Hortinstein on 2007-03-27
Could someone help me add this to my routing table preferably a script

I have the top line i just need the bottom two

Code:
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
216.98.230.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         216.98.228.1    0.0.0.0         UG    0      0        0 eth1


```

---

### Post by lloyd_b on 2007-03-27
> **Hortinstein said:**
> Could someone help me add this to my routing table preferably a script

I have the top line i just need the bottom two

Code:
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
216.98.230.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         216.98.228.1    0.0.0.0         UG    0      0        0 eth1


```

```
sudo route add -net 169.254.0.0 netmask 255.255.0.0 metric 1000 eth1
sudo route add default gw 216.98.228.1 eth1
```

That said - why?  If your system is properly configured, you shouldn't have to manually add any routes.  If you post the contents of the file "/etc/network/interfaces", we can probably work out how to have this done automatically (I'm assuming that you're using static IP addresses, as DHCP should be handling all of this for you).

Lloyd B.

---

### Post by Hortinstein on 2007-03-27
sudo route add default gw 216.98.228.1 eth1

this one doesnt work the other one does....this one says network unreachable...

ill post my interfaces file right after this

---

### Post by Hortinstein on 2007-03-27
```
auto lo
iface lo inet loopback



#iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp









iface eth1 inet static
address 216.98.230.20
netmask 255.255.255.0
network 216.98.230.0
broadcast 216.98.230.255
gateway 216.98.225.1
dns 216.98.228.1
wireless-essid PGD_1

auto eth1

#auto eth0

iface eth0 inet dhcp



```

---

### Post by lloyd_b on 2007-03-27
> sudo route add default gw 216.98.228.1 eth1

this one doesnt work the other one does....this one says network unreachable...

Oops, wasn't reading carefully enough.  The problem with that gateway is that it is not on a defined network (216.98.228.0, while you're on 216.98.230.0).  So the question is, how are the packets supposed to reach the gateway without going through a gateway?

If the 216.98.228.0 network *is* directly reachable from your machine, try:
```
sudo route add -net 216.98.228.0 netmask 255.255.255.0 eth1
sudo route add default gw 216.98.228.1 eth1 
```

Now, as for the "interfaces" file:
```
iface eth1 inet static
address 216.98.230.20
netmask 255.255.255.0
network 216.98.230.0
broadcast 216.98.230.255
gateway 216.98.225.1
dns 216.98.228.1
wireless-essid PGD_1
```

You've got some issues here.  The "network" line you have is redundant - the IP address and netmask will automatically add this network (it doesn't hurt to have it, it just not necessary).

In this case, you have your gateway listed as 216.98.225.1, while in the "route" output you listed previously it was set to 216.98.228.1.  You need to sort out which it is, and add an additional "network" line so that your computer knows how to reach the gateway.

i```
face eth1 inet static
address 216.98.230.20
netmask 255.255.255.0
network 216.98.230.0
broadcast 216.98.230.255
[B]network 216.98.225.0
gateway 216.98.225.1[/B]
dns 216.98.228.1
wireless-essid PGD_1
```
or
```
face eth1 inet static
address 216.98.230.20
netmask 255.255.255.0
network 216.98.230.0
broadcast 216.98.230.255
[B]network 216.98.228.0
gateway 216.98.228.1[/B]
dns 216.98.228.1
wireless-essid PGD_1
```

Once you've made the appropriate changes to the file
```
sudo /etc/init.d/networking restart
```
will stop networking, and restart it with the new settings.

Finally, that "169.254.0.0" network you have added is a bit weird - you can add a basic network definition with "network 169.254.0.0" to the interfaces file, but I have no clue as to how to get that metric (1000) set without messing up the metric for the other networks.

Lloyd B.

---

### Post by Hortinstein on 2007-03-27
ok i will try this later today and fill in on results

---

### Post by Hortinstein on 2007-03-27
ok when i try each of those it doesnt work....says "failed to bring up wlan0"
than "SIOCADDRT:NETWORK is unreachable"
than "Failed to bring up eth1"

i dont get it....the routes havent changed either

---

### Post by lloyd_b on 2007-03-27
Okay, I think I gave you some bad info on the last post - it seems that the multiple "network" definitions is a no-no.

Let's step back a bit.  Could you clarify exactly how your network is structured?  Specifically:
1.  Where is your gateway? 216.98.225.1, 216.98.228.1, something else?
2.  Are all of the "216.98.x.x" networks on the same physical network?  
3.  What is that 169.254.x.x network?

Here's what I think *should* work, assuming that the gateway is in fact at 216.98.228.1.

New "/etc/network/interfaces" file:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
     address 216.98.230.20
     netmask 255.255.255.0
     broadcast 216.98.230.255
     wireless-essid PGD_1
     post-up /etc/network/custom

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

File "/etc/resolv.conf":
```
nameserver 216.98.228.1
```

New file: "/etc/network/custom".  You MUST have root permission to create this file (i.e. "sudo nano /etc/network/custom")
```
#!/bin/sh
route add -net 216.98.228.0 netmask 255.255.255.0 eth1
route add -net 169.254.0.0 netmask 255.255.0.0 metric 1000 eth1
route add default gw 216.98.228.1 eth1
```
After creating the file, you need to make it executable:
```
sudo chmod 700 /etc/network/custom
```

That *should* provide full connectivity for your machine.  Note that your routing table will NOT be exactly like your original example - there'll be one extra route, for the 216.98.228.0 network.  I'm guessing that the routing table you provided was from a Windows machine (which seem to be a bit more tolerant of certain issues that Linux).

After making these changes, run "sudo /etc/init.d/networking restart".  If there are any errors, if possible capture and post them.

Lloyd B.

---

### Post by Hortinstein on 2007-03-28
sweet thanks for the good info....ill check it out when i get home!

---

