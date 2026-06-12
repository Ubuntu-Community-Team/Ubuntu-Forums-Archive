---
title: "Ubuntu 6.10 machine name not registered with DHCP server"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by BobSelby on 2006-12-15
I'm a Ubuntu newbie and have just installed 6.10 and to my pleasant surprise it all went very smoothly :-)

However, I have encountered one problem that I don't seem to be able to solve.  I have configured the network as "use DHCP" and set a host name and while the system is able to get an IP address etc OK the local host name is not registered with my DHCP server.

I can access the local net and the internet from the Ubuntu box and I can ping the Ubuntu box by IP address from both my firewall system and a windoze box on the local net.  But I cant ping by name from either.

Looking on the firewall's config screen it is the only box that hasn't got a name associated with its entry.   The firewall is FreeSco v035 BTW (linux distro).

Any idea how I can overcome this ??
TIA

---

### Post by samiux on 2006-12-15
You need a DNS for your intranet?

Samiux

---

### Post by BobSelby on 2006-12-15
FreeSco has a DNS server built in that talks in turn to the ISPs DNS server and provides a cache.  FreeSco's DNS server synchronises with its DHCP server so that local machines names can be resolved without intervention.

The problem is that if Ubuntu doesnt register its host name when it does the DHCP transaction the name will never be associated in the local DNS.

I think that makes sense :-)

---

### Post by Iowan on 2006-12-15
I have a '486 FREESCO router (033-035?).  It is my DNS server, but I moved DHCP to another box to lighten the load.
You probably need to edit **/etc/dhcp3/dhclient.conf**
```
sudo gedit /etc/dhcp3/dhclient.conf
```
 uncomment  the line ```
#send host-name "andare.fugue.com";
```  and insert your hostname.

---

### Post by BobSelby on 2006-12-16
Thanks - that worked a treat :-)

---

