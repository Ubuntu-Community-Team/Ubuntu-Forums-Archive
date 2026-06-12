---
title: "Can't enable eth0...."
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by thane777 on 2005-04-19
hi -
I am a ubuntu newbie.... a convert from Mandrake.  I am actually using kubuntu since I am a kde user.

I have 2 nics in my box, eth0 to my local network and eth1 to my cable modem.  The problem is that I cannot enable eth0.  I try to using Control Center; Internet and Network:Network Settings.

eth1 comes up fine.  It is getting its IP address from the cable modem (dhcp).  I set eth0 to a static address and it does not enable for some reason.  It worked fine under Mandrake and Windows but not here.

Any ideas?

TIA -


thane

---

### Post by siebzehn on 2005-04-19
[QUOTE=thane777]hi -
I am a ubuntu newbie.... a convert from Mandrake.  

I have 2 nics in my box, eth0 to my local network and eth1 to my cable modem.  The problem is that I cannot enable eth0.  I try to using Control Center; Internet and Network:Network Settings.

eth1 comes up fine.  It is getting its IP address from the cable modem (dhcp).  I set eth0 to a static address and it does not enable for some reason.  It worked fine under Mandrake and Windows but not here.

Any ideas?

TIA -


thane[/QUOTE]
 Please post your  /etc/network/interfaces   file  so i can check your configuration

---

### Post by thane777 on 2005-04-19
Here is the info from my /etc/network/interfaces file:

dave@linbox:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp

I see eth0 is totally missing.  What is the proper way to add them in?

Thanks!

thane

---

### Post by alastair on 2005-04-19
Maybe hand edit and restart the device i.e. add :

```

iface eth0 inet static
        address <IP>
        netmask <MASK>
        network <NETWORK>
        broadcast <BROADCAST>
        gateway <GW IP>

```

Then :

sudo ifup eth1

---

### Post by thane777 on 2005-04-19
[QUOTE=alastair]Maybe hand edit and restart the device i.e. add :

```

iface eth0 inet static
        address <IP>
        netmask <MASK>
        network <NETWORK>
        broadcast <BROADCAST>
        gateway <GW IP>

```

Then :

sudo ifup eth1[/QUOTE]

I added the first 3 lines you list but I don't know what to put for the others (network, broadcast and gateway)

eth0 is to serve as a gateway to my laptop so I think I leave that blank.
Do I need to fill in network and broadcast?


Thanks!


thane

---

### Post by alastair on 2005-04-19
Maybe you don't need them - try bringing the interface up without.

If no go - the others are straightforward e.g. mine is :

```

iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

---

### Post by siebzehn on 2005-04-20
Or you can just try to bring it up with DHCP.  Put this in   /etc/network/interfaces

iface eth0 inet dhcp

auto eth0




and then just tipe  "sudo ifup eth0"   and tell me what happens

---

### Post by nautilus on 2005-04-20
Well, the static section should be fine, but if you want it to come up automatically, place this line there as well:

```
auto eth0
```

---

### Post by thane777 on 2005-04-20
[QUOTE=alastair]Maybe you don't need them - try bringing the interface up without.

If no go - the others are straightforward e.g. mine is :

```

iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```[/QUOTE]


All's well now.  THanks.  I just added everything except the gateway and it came up fine.  

Thanks for your help.


thane

---

