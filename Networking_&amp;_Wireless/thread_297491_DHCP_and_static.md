---
title: "DHCP and static"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by string on 2006-11-11
Hi all,

I have a Linksys router and to make my port forwarding stuff, I set a static IP on my Ubuntu :
```

[...]
# The primary network interface
iface eth1 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1
[...]

```

in my /etc/network/interfaces

It sets the good ip address when I /etc/init.d/networking restart but after a while, it changer the ip as if a dhcp request was made.

I let the DCHP enabled on my linksys router (for other pcs of my network that I don't care of the port forwarding). But I should be able to have it working this shouldn't I ?

I ask here because I'm not sure whether it's a problem setting on the router side or the os side.

thanks.

---

### Post by dmizer on 2006-11-11
funny thing about dhcp/static ip addressing.  for dhcp, your router assigns all the ips for your network.  if you assign one computer as static ip on a dhcp network, your router doesn't have a record that the ip address has been assigned and treats it like an open ip.  then when you turn another computer on, the router can assign assign the new machine the same ip address.

some routers have the capability of reserving a specific ip address according to mac addresses, which allows you to have a "static" ip for your server while retaining the convenience of a dhcp network with the rest of your connections.

you might try playing with the settings in your router.  also, usually (not always) routers start assigning ips from lowest to highest.  so if your range starts at x.x.x.110 and goes to x.x.x.120 for example, the router will assign the first free ip address (x.x.x.110) to the new machine.

so with that in mind you might (might) be able to get away with assigning the largest available ip address as your static ip.  dunno.

finally, some routers are capable of handling netbios names.  so they can forward port 80 to "ubuntuserver" rather than x.x.x.x ip address.

---

### Post by string on 2006-11-11
> funny thing about dhcp/static ip addressing. for dhcp, your router assigns all the ips for your network. if you assign one computer as static ip on a dhcp network, your router doesn't have a record that the ip address has been assigned and treats it like an open ip. then when you turn another computer on, the router can assign assign the new machine the same ip address.

I know, but it's not a problem, the router has a setting : DHCP range, and the static IP I have on this particular machine is out of it.

---

### Post by dmizer on 2006-11-13
try posting the entire contents of your interfaces file.  also post the results of ifconfig (or iwconfig if you're wireless).

---

### Post by stream303 on 2006-11-13
Hmm.. how about a different subnet like
192.168.2.1 as the box's address...

---

