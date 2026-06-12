---
title: "how to change the MAC-address permanently?"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by insta on 2007-04-05
Hello there!

Unfortunately my internet-connection is bound to the MAC-address of my old NIC which died a while ago. I therefore need to permanently change the MAC-address of the NIC I am using now.

this works fine as long as I do it manually:
```

ifconfig eth0 down hw ether <MAC-address>
ifconfig eth0 up

```

I have to shut down the network connection using the Network-Manager-Applet" beforehand, though.

However if I try to do it with an entry in /etc/network/interfaces like this
```
auto eth0
iface eth0 inet dhcp
hwaddress ether <MAC-address
```

it obstinately ignores this and uses the NIC's hardware-MAC instead
Likewise a script in /etc/network/if-up.d or .../if-pre-up.d using ifconfig didn't work.

What goes wrong? How can I fix it? :confused:

---

### Post by Floppyjoe on 2007-04-05
There is a utility called macchanger that you can download with Synaptic Package Manager. I have not used it so I don't know how it works. I think it is a terminal based utility. It allows you to change the mac address of of network interfaces.

---

### Post by insta on 2007-04-05
> **Floppyjoe said:**
> There is a utility called macchanger that you can download with Synaptic Package Manager. I have not used it so I don't know how it works. I think it is a terminal based utility. It allows you to change the mac address of of network interfaces.

macchanger changes the MAC until next reboot, just as ifconfig does ... alas no solution for me

Doesn't anyone have an idea on that? There must be a solution.

---

### Post by hartl_vienna on 2007-04-15
I' ve the same problem. Does anyone have a solution? :confused:

---

### Post by albs on 2007-04-15
Hey guys,

I could be totally off topic, but esentially the MAC address is something that is unique to that particular NIC.  Another name for a MAC address is a Burned In Address.  It's a code which is set according the manufacturer, product and the device itself.

You could get software to mask the MAC with another address, but not really change it.

---

### Post by SleepWalkerX on 2007-10-23
is there a working script that can change it before dhclient runs on startup?  i too would like to change my mac 'permanently'.

---

### Post by froy02 on 2007-10-23
You can not really change a MAC address. It comes with the peripheral from the manufacturer.  A DHCP server when configured to automatically assign ip address all you have to do is plug in to the router.  If you can to that all you have to do is install the driver and plug in your nic.
 
Or configure your new mac address for an ip address.  Not the other way around.

---

### Post by SleepWalkerX on 2007-10-23
That's why I mean 'permanently' on the software side.  Like maybe a script to do:

```
ifconfig eth0 down hw ether <MAC-address>
ifconfig eth0 up
```

before my dhcp client kicks in.

---

### Post by IamAcoconut on 2007-12-05
> **SleepWalkerX said:**
> That's why I mean 'permanently' on the software side.  Like maybe a script to do:

```
ifconfig eth0 down hw ether <MAC-address>
ifconfig eth0 up
```

before my dhcp client kicks in.
Maybe insert this to /etc/init.d/networking ?
I'll give it a try.

---

