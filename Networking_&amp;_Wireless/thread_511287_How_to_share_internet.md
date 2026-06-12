---
title: "How to share internet ?"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by NovaNine on 2007-07-27
Hi people !
I was wondering, how do you do to share internet to a number of XP computers through an Ubuntu server ?  The server has two LAN cards, so one is an "intake" from the modem, and the other one i want to use as a way to share the internet to the rest of the network. Here's how the network goes =>

Modem  => Router => | <= => Ubuntu Server
[COLOR="White"]Modem  => Router =>[/COLOR] | => Rest of the network

Thanks for any help :)

---

### Post by dmizer on 2007-07-27
you have a router.  share your connection through your router just as you've outlined.

the purpose of internet connection sharing is for when you don't have a router as in this diagram:

Modem => Ubuntu server => hub/switch => | <= Rest of network

several reasons for this kind of set up.  here are a few:
1) for when you have a "Rest of network" large enough (100+ pc's) to necessitate an intelligent switch and an entire computer dedicated to route traffic to the outside world.
2) as a temporary stand in while your main NAT device is being replaced/repaired/upgraded
3) too cheap to purchase a router
4) dial up internet connection

or in other words.
you don't need internet connection sharing.

---

### Post by NovaNine on 2007-07-27
The problem is that my ISP only has given me one static IP address. This is why I need my network to take the internet from one computer, so to have their IP addresses as local IP (192.168.0.x) :)

---

### Post by dmizer on 2007-07-28
yes ... a **router** gives you a local ip of 192.168.0.x ... or 192.168.1.x

so this:
Modem => Router => | <= => Ubuntu Server
[COLOR="White"]Modem => Router =>[/COLOR] | => Rest of the network

will allow all your computers on your network to browse the internet at the same time.

a **router** does network address translation which allows multiple computers access to the same internet connection.
a **hub** does not do network address translation.  it requires you to have a dhcp server to hand ip addresses to the network.
a **switch** is similar to a hub except that a switch is intelegent and keeps track of which traffic belongs to what computer.

the only time you need a dhcp server to hand dynamic local ip addresses to your local network is if you're using a hub or a switch.

---

