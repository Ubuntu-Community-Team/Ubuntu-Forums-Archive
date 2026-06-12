---
title: "What command do I type into terminal to get a list of network cards?"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by grs on 2008-09-05
What command do I type into terminal to get a list of network cards?
I've just installed Ubuntu Server and I don't think the on-board NIC is compatable (Asus M2A-VM series motherboard). If I type:

#cat /etc/network/interfaces

I get:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by Ayuthia on 2008-09-05
> **grs said:**
> What command do I type into terminal to get a list of network cards?
I've just installed Ubuntu Server and I don't think the on-board NIC is compatable (Asus M2A-VM series motherboard). If I type:

#cat /etc/network/interfaces

I get:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

You can try:
```
lshw -C network
```

If that does not produce any results, you can list out all your pci cards:
```
lspci -nn
```Just look for something that says Network Controller or Ethernet Controller.

---

### Post by dodle on 2008-09-05
```
iwconfig
```That's the only one that I know of off-hand, but there are probably better ones.

---

### Post by grs on 2008-09-05
```

lshw -C network

```

Gives me a list of network card info. The info is too much to fit on the whole screen, how can I scroll up to see the first bit?
I can't see the detals for the on-board NIC but the PCI NIC I stuck in says something about been disabled.

The second command again has too much info for one screen so I can't read it all.

---

### Post by Ayuthia on 2008-09-05
> **grs said:**
> ```

lshw -C network

```

Gives me a list of network card info. The info is too much to fit on the whole screen, how can I scroll up to see the first bit?
I can't see the detals for the on-board NIC but the PCI NIC I stuck in says something about been disabled.

The second command again has too much info for one screen so I can't read it all.

I am assuming that you are not using any GUI.  If that is the case, there are two ways.  You should be able to scroll up by using shift and Page Up.  The other option would be to do the following:
```
lshw -C network|less
```
You should be able to use the arrow keys to scroll.

---

### Post by grs on 2008-09-05
Thats right. I don't have a GUI setup, just terminal. Once I get the network sorted I will connect to the Ubuntu Server by putty.
The network device that should be are and I can see the on the Linksys Router.
I'm going to setup the extra drives I have mount as well as Samba and then come back to the network.

---

