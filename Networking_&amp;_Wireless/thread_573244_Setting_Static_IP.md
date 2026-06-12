---
title: "Setting Static IP"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by CarlosinFL on 2007-10-11
Guys - I need to change my Default Gateway on my PC. Currently my machine is setup dynamicly and getting everything from DHCP and DNS however I would like to add my info in staticly but not sure the correct config sequence.

Right now I have added my **[SIZE="4"]/etc/network/interfaces[/SIZE]** config file below:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by helgman on 2007-10-11
Start with writing down the information you are going to use. Such as:

IP address
netmask
gateway
DNS-server

In most cases this is enough.

Then edit **/etc/network/interfaces**

```
auto eth0
iface eth0 inet static
address <ip address>
netmask <netmask>
gateway <gateway>
```

Now I've seen DNS set up in the interfaces file but I've never tried it, so I'd put it in **/etc/resolv.conf**:

```
nameserver <IP address of DNS server>
```

You can add as many as you want (but I think only the three first are used or something like that).

Before you do all this make sure to look at the files (maybe even making a backup if something goes terribly wrong).

Good luck!

Helgman

---

### Post by CarlosinFL on 2007-10-11
Once I set everything up staticly, how do I refresh for the new settings to take effect as I have done this however my DG still is the old 10.1.1.1 rather than the staticly set DG of 10.1.1.231.

---

### Post by Jose Catre-Vandis on 2007-10-11
Ensure your router/dhcp/lan server etc is set to allow IP's with that number

To restart networking enter this command in a terminal
```
sudo /etc/init.d/networking restart
```

or just reboot

check your settings with
```
ifconfig
```

---

### Post by CarlosinFL on 2007-10-11
> **Jose Catre-Vandis said:**
> 

check your settings with
```
ifconfig
```

The only change going from dynamic to static is my default gateway so once I restart networking, how do I verify my new static gateway is being used vs my old dynamic gateway? The "ifconfig" does not show me the gateway IP sadly.

---

### Post by helgman on 2007-10-11
```
route
``` or ```
route -n
``` and look for *destination* default/0.0.0.0.

Regards,
Helgman

---

### Post by Jose Catre-Vandis on 2007-10-16
Depending on your router, you can usually use the router default for the gateway, unless you are wanting to use a different one. e.g. if your router is 10.1.1.1 then your gateway will be 10.1.1.1

---

### Post by johnny9794 on 2007-10-28
address <ip address>   <for that part what ip should go in there, for example 192.168.2.10 or the main external ip?

---

### Post by helgman on 2007-10-28
> **johnny9794 said:**
> address <ip address>   <for that part what ip should go in there, for example 192.168.2.10 or the main external ip?

The IP address you want that interface to use should go in there. So if you want 192.168.2.10 then yes, put 192.168.2.10 there. If it's connected directly to the Internet then put whatever address your ISP has given you.

Regards,
Helgman

---

