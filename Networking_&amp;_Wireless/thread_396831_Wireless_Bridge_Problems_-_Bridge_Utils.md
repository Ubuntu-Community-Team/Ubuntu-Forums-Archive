---
title: "Wireless Bridge Problems - Bridge Utils"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Shamem on 2007-03-29
I'm trying to set it up my ubuntu edgy server to act as a wireless bridge between the wireless network at my hostel and my wired lan my computers are on.

At the moment this task is being preformed by my laptop running windows, but i would like to be able to actualy use my laptop as a laptop. I have installed a wireless card on my server, and installed the windows drivers. It works fine, but when i try to use bridge-utils to bridge the connections, all the net dies.

I have spent the last 7 hours(literaly) searching the net for a solution, but most of the info is about setting up a router or access point, not a bridge, and my attempts of converting the provided information to relivent steps on my computer have failed.

Here is the /etc/network/interfaces file that i eventualy came up with(one fo the many revisions anyway), which does not seem to work.

I want my server on 192.168.3.50(ie, i want to bridge set to that)
eth0 is my servers ethernet port
wlan0 is the servers wireless lan adapter.
Router i am trying to conect to is at 192.168.3.1

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

# The primary network interface

auto eth0
iface eth0 inet static
#    address 192.168.3.48
#    netmask 255.255.255.0
#    gateway 192.168.3.1

auto wlan0
iface wlan0 inet dhcp
    wireless-essid Zion
    wireless-key **********
#    address 192.168.3.49
#    netmask 255.255.255.0
#    gateway 192.168.3.1

auto br0
iface br0 inet static
    address 192.168.3.50
    network 192.168.3.0
     netmask 255.255.255.0
     broadcast 192.168.3.255
      bridge-ports wlan0 eth0


```After setting this file(and its many revisions), i stop the networking interfaces with
```
 sudo ifconfig eth0 down 
``` etc.
Then i restart networking with
```
 sudo /etc/init.d/networking restart 
```If anyone can find the problem with this, or some other thing i have done, it would be much apreciated.

o, also, in my hunt for answers routing has been sugested as an alternative to using bridge-utils, but once again i havn't been able to find enough info. Can routing be used to provide the same service as bridging the conections?

thanks,

---Shamem

---

### Post by chinmaykamat on 2007-03-30
Try this link


[http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)

could be helpful.....also look at the links

---

### Post by Shamem on 2007-03-30
That is what i tried origonaly, with no luck. It doesn't seem to matter if i am using brctrl to set up the bridge, or the /etc/network/interfaces, the wireless still doesn't work.

Is there something wrong with my setup? or is bridging just not suported in my wireless card?

Also, anyone know if i can fix the problem with routing?

thanks, 

---Shamem

---

### Post by Shamem on 2007-03-30
Ok, i've been doing some more looking around, and it seems that routing may work. However, once again, everything i can find doesn't realy help that much. Most send you on an infinite series of links about problims vaugely similar to your own. I realy do not have the time at the moment to sort through all this data and try to work out what is actualy going on, so it would be great if some one could tell me what changes i need to make to my routing tables, and anything else that is required. How to do those changes, and make them happen every boot would also be apreciated.

ok, here is my current /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

# The primary network interface

iface eth0 inet static
	address 192.168.3.50
	netmask 255.255.255.0
	gateway 192.168.3.1
	network 192.168.3.0
	broadcast 192.168.3.255

iface wlan0 inet static
	wireless-essid Zion
	wireless-key **********
	address 192.168.3.49
	netmask 255.255.255.0
	gateway 192.168.3.1

auto eth0

auto wlan0

```

My current routing table:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.3.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.3.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.3.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.3.1     0.0.0.0         UG        0 0          0 eth0

```

The server is conected to my network through eth0. Eth0's ip is currently 192.168.3.50. It is also conected to my hostels wireless network router via a network card, wlan0, at 192.168.3.49. the wireless router has the address 192.168.3.1, and is conected to the internet, and to other computers on teh wireless network.

What i want is full conectivity between the internet. my local network, and the wireless hostel network. Ie, computers on my network need to be able to access my server, the internet, and computers on the wireless network. Computers on the wireless network also need to be able to access my server, and computers on my local network.

any help would be much apreciated.

---shamem

---

### Post by Shamem on 2007-04-04
Anyone know what i need to do?

help would be much apreciated.

---Shamem

---

