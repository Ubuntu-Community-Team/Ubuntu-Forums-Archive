---
title: "[SOLVED] Routing woes"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Deicist on 2008-07-03
I have a minor problem with my Routing.  I followed a guide on t'internet to embed a seamless RDP connection to a VirtualBox XP guest on my desktop.  This works perfectly, and I've managed to 'bridge' my wireless connection to the Virtual machine.  However, the method used to enable the bridge kills my Host's netowrking.  Once the bridge is up I can hit addresses from the Guest, but not the Host.  

Here's the script I'm using to bring the bridge up:

```

#!/bin/sh
sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u paul
ip link set tap0 up
ip addr add 192.168.1.108/24 dev tap0
parprouted wlan0 tap0
route add -net 192.168.1.0 netmask 255.255.255.0 tap0

```

wlan0 is my network interface
192.168.1.108 is the Guest IP address.  

I'm guessing (although I really don't have much idea) that the problem is the route added at the end of the script... it seems to be directing all traffic aimed at the 192.168.1. subnet to the tap0 interface.  However, since my DNS and gateway are on that subnet the host can't see them :/

---

### Post by ilrudie on 2008-07-03
Post the output from 
```
netstat -rn
```
Please run this command both before and after setting up your bridged connection to the VirtualBox.

As a side note does VirtualBox not have a built-in way to do this?  I have never used VirtualBox but VMware Player on windows and Fusion on Mac both had the option to bridge or NAT.

---

### Post by Deicist on 2008-07-03
before:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.30    0.0.0.0         255.255.255.255 UH        0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

```


After
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH        0 0          0 wlan0
192.168.1.30    0.0.0.0         255.255.255.255 UH        0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 tap0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

```

After running the script I can browse the net, but I can't connect to servers on the 192 subnet via RDP / Citrix from the Host system.

192.168.1.30 is my DNS server btw, I see from the 'after' code that there's a route setup pointing that to wlan0, so I guess what I need to do is add routes for other addresses I want to hit from the host machine.

I need to be able to access 192.168.1.21 as well, so I tried doing:

```

sudo route add -net 192.168.1.21 255.255.255.255 wlan0

```

but it didn't seem to make any difference (still can't ping / hit that server from the Host)

---

### Post by ilrudie on 2008-07-03
try
```

sudo route add -host 192.168.1.21 wlan0

```Im not sure what the code you posted would do.  I'm pretty sure you meant to do 
```

sudo route add 192.168.1.21 netmask 255.255.255.255 wlan0

```which should make the same routing entry as my other suggestion.

Also out of :
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 tap0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 tap0
only the first one counts.

---

### Post by Deicist on 2008-07-03
Still no go.

I still can't hit that host from the host machine.  

Also, those multiple routes are added automagically when I run that script.  I've not added any routes manually.

---

### Post by ilrudie on 2008-07-03
> **Deicist said:**
> 
I still can't hit that host from the host machine.  


Are these two different machines?  You used host too much and I'm confused now.
So far we have:
192.168.1.108=VM
192.168.1.21=?
?=physical box hosting the VM

Anyways... post the netstat -rn after running the route add command with the bridge up.  Also post an ifconfig -a.  Most likely what is happening is you have added a route below the line that sends all local traffic out the second interface (tap0). and tap0 is not working for some reason.  Does this only kill your connection to hosts on your lan or does it kill your internet as well?

Also can you post a link to the tutorial you read so I can also read it and see if I can't figure out what it is trying to accomplish by sending all local traffic out this virtual interface?

---

### Post by tjwallace on 2008-07-03
If you want a bridge do you not have to create a br0 device?

Here is the code I use to create a bridge and tap device:
```

#!/bin/sh
# RUN THIS AS ROOT USER!
# login name of HOST system
USERNAME=jeff

chown root.vboxusers /dev/net/tun
chmod g+rw /dev/net/tun

ifconfig wlan0 0.0.0.0 promisc
brctl addbr br0
brctl addif br0 wlan0

dhclient br0
# if you want the bridge to have a static IP use below
#ifconfig br0 192.168.1.10 netmask 255.255.255.0 up
#route add -net 192.168.1.0 netmask 255.255.255.0 br0
#route add default gw 192.168.1.1 br0

VBoxTunctl -b -u $USERNAME

ifconfig tap0 up
brctl addif br0 tap0

```

Maybe give it a try and see what happens.

---

### Post by Deicist on 2008-07-04
> **tjwallace said:**
> If you want a bridge do you not have to create a br0 device?

Here is the code I use to create a bridge and tap device:
```

#!/bin/sh
# RUN THIS AS ROOT USER!
# login name of HOST system
USERNAME=jeff

chown root.vboxusers /dev/net/tun
chmod g+rw /dev/net/tun

ifconfig wlan0 0.0.0.0 promisc
brctl addbr br0
brctl addif br0 wlan0

dhclient br0
# if you want the bridge to have a static IP use below
#ifconfig br0 192.168.1.10 netmask 255.255.255.0 up
#route add -net 192.168.1.0 netmask 255.255.255.0 br0
#route add default gw 192.168.1.1 br0

VBoxTunctl -b -u $USERNAME

ifconfig tap0 up
brctl addif br0 tap0

```

Maybe give it a try and see what happens.

According to the docs (and my testing) bridges don't work with wireless connections.

---

### Post by tjwallace on 2008-07-04
Sorry yes you are right.  I'm guessing you are reading from [http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html) ?

Have you tried without doing the route command in your script?

---

### Post by Deicist on 2008-07-04
Okay, problem solved... I changed the route from:

```

route add -net 192.168.1.0 netmask 255.255.255.0 tap0

```

to

```

route add -net 192.168.1.150 netmask 255.255.255.255 tap0

```

Now only requests for that IP address are routed through the tap interface, everything else goes through the wireless as normal.

Cheers for the help guys :)

---

### Post by escipio on 2008-07-20
Hello:

I tried to do the same thing, but I was unable of making the net working in the guest. Which values for IP address, gatway and netmask should I use in the guest? 

I tried using a new ip address, the ip address used in the route command, but nothing.
The only thing I can do is a ping to the host computer, and from the host computer a ping to the guest.

Any help would be appreciated.

Thank you in advance.

Escipio

---

### Post by escipio on 2008-07-22
Problem solved.

The trick was using, in the guest, 192.168.1.1 as a gateway, instead of 192.168.1.0.

Thank you, very much. This thread has been a good help.

---

