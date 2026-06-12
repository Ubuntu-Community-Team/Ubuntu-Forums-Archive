---
title: "Setup broadband connection with static IP"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-01-06
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
Xfce4 desktop

Connection:
Ubuntu server --> Router --> Modem --> ISP

On running Static IP, performed;
Righ_click Xfce desktop --> System --> Networking
starting Network-admin

Selected "Ethernet connection" --> Properties
starting "Interface properties" window

Filled in;
Configuration: Static IP address
IP address:  192.168.0.10
Subnet mask:  255.255.255.0
Gateway address: 192.168.0.1
Clicked OK
Then I was on my way.

Remark:
IP address:  192.168.0.10
is the virtual IP on router which was supplied by ISP and pre-set;
Virtual IP: 192.168.0.10 to 192.168.0.60

I suppose this is the front-end/GUI.  I'm interested to know which file on the backend I have to edit changing this settings.  TIA

Further more, can I leave out the router making the connection as;
Ubuntu server --> Modem --> ISP

If Yes, please advise how to change the settings to take effect,  Tks


B.R.
satimis

---

### Post by mojoman on 2007-01-06
Have a look at /etc/network/interfaces. This file should contain the vital information you're looking for. Also, have a look at /etc/resolv.conf, this should contain your nameservers (should probably point to your router).

You should be able to bring up the network with the command ```
ifconfig ra0 up
``` or ```
ifconfig eth0 up
``` (or whatever your network connection is named), however my laptop won't have any of that and will only settle for a restart.

/mojoman

---

### Post by satimis on 2007-01-06
Hi mojoman,

Tks for your advice.

> 
Have a look at /etc/network/interfaces. This file should contain the vital information you're looking for. 

Before I have been looking around on this file and can't ascertain whether it is the right one.

$ cat /etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
     address 127.0.0.1
     netmask 255.0.0.0

auth eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0

#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

iface ppp0 inet ppp
provider ppp0

```
I suppose following entries being necessary;```

auth eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

```

What about the other data on this file?  Can I delete all of them?  I don't need pppoe anymore.

Remark:
address 192.168.0.10
is the Virtual IP address on the router which is supplied by ISP and pre-set with;```

Virtual IP address 192.168.0.10 to 192.168.0.60

```


> 
Also, have a look at /etc/resolv.conf, this should contain your nameservers (should probably point to your router).

$ cat /etc/resolv.conf```

nameserver 202.14.67.4
nameserver 202.14.67.14
lookup file bind
#search com
#nameserver 204.11.126.131
#nameserver 64.125.134.133
#nameserver 64.125.134.132
#nameserver 208.185.179.218

```
The nameservers 202.14.67.4/14 are correct.  Can I delete the rest?  Tks.


> 
You should be able to bring up the network with the command ```
ifconfig ra0 up
``` or ```
ifconfig eth0 up
``` (or whatever your network connection is named), however my laptop won't have any of that and will only settle for a restart.

$ /etc/init.d/networking status```

Usage: /etc/init.d/networking {start|stop|restart|force-reload}

```
I suppose I can restart network here.


How to edit the file /etc/network/interfaces, if I make the server connected directly to the Modem without the router?  Tks.

B.R.
satimis

---

### Post by koenn on 2007-01-06
> make the server connected directly to the Modem without the router?
why would you want to do this ? are you sure it's a good idea ? 

If you use the words "router" and "modem" correctly (you seem to, but a lot of people here don't), you want to connect that server directly to the internet, with a public IP address, is that it ?

---

### Post by mojoman on 2007-01-06
I suppose you can delete the pppoe if you don't need it but whatever you do don't delete the loopback interface. I'm not sure about the other stuff. I don't have that in my files but that doesn't necessarily mean anything. Do you really need to delete it? Anyway, if you can't stand having it there you can try commenting it out before be adding # in front of the lines you want to delete. Anyting after # on a line is not read by the system. Reboot and run it for a while, and if all is good, well, then maybe you don't need it. But again, I would be very careful...

/Mojoman

ps: the # is a nefty little tool that is used to have all sort of information in the system files that you might want but that the system don't need, e.g. explanatory stuff about the different options. ds.

---

