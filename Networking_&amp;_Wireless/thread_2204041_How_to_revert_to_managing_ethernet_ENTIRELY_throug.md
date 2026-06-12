---
title: "How to revert to managing ethernet ENTIRELY through /etc/interfaces?"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by mattlach on 2014-02-06
Hey all,

I've noticed that in recent releases /etc/interfaces only contains the loopback interface.  Everything else seems managed somewhere else, potentially entirely through the graphical Network management screen.

I am trying to do some 802.3ad bonding using ifenslave, and in order to do this, I need full control back in /etc/interfaces.

This worked great on my 12.04 LTS Ubuntu Server install, but the desktop version now handles /etc/interfaces differently.

Can anyone tell me the steps I need to go through in order to return all management to /etc/interfaces?

Will it work, if I just start adding lines here, or are the other files I need to edit in order to add the eth0 and eth1 interfaces first, before configuring them in /etc/interfaces?

Much obliged,
Matt

---

### Post by The Cog on 2014-02-06
As far as I know, if you configure an interface in /etc/network/interfaces, then NetworkManager will defer to that and will ignore that interface. So just configure them all in /etc/network/interfaces. And maybe reboot - I don't know how else to get NM to realise you want it to leave them alone now.

---

### Post by SeijiSensei on 2014-02-06
Just the other day I defined the eth0 interface in /etc/network/interfaces.  It no longer appears in Network Manager.  (This is on Kubuntu 14.04; YMMV.) 

Isn't is possible to uninstall Network Manager altogether and just use /etc/network/interfaces?  I've thought about doing that, but it seems easier to let NM handle my wifi connection.

---

### Post by mattlach on 2014-02-06
> **SeijiSensei said:**
> Just the other day I defined the eth0 interface in /etc/network/interfaces.  It no longer appears in Network Manager.  (This is on Kubuntu 14.04; YMMV.) 

Isn't is possible to uninstall Network Manager altogether and just use /etc/network/interfaces?  I've thought about doing that, but it seems easier to let NM handle my wifi connection.

That is an interesting thought.   Presumably it is listed as a dependency of the base Ubuntu system in Apt though, complicating things.

---

### Post by mattlach on 2014-02-06
Thanks for the suggestions.   I will try just adding my eth0 and eth1 interfaces and see what happens.

I was concerned it might not work, as I didn't know if the move towards network manager also affects /etc/udev/rules.d/70-persistent-net.rules, and if I had to go in there and manually add ethernet devices, add mac addresses and painful stuff like that.  (bad memories)

Thanks again.

---

### Post by chili555 on 2014-02-06
> Isn't is possible to uninstall Network Manager altogether and just use /etc/network/interfaces? I've thought about doing that, but it seems easier to let NM handle my wifi connection. Entirely possible and done on the computer I am answering on. My file is:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```It's only a bit more complex with wireless.>  /etc/udev/rules.d/70-persistent-net.rules, and if I had to go in there and manually add ethernet devices, add mac addresses and painful stuff like thatOuch! Not needed. Mine is untouched.

---

### Post by mattlach on 2014-02-06
Thanks guys!

I just added the eth0 and eth1 configuration and it worked like a charm!

---

