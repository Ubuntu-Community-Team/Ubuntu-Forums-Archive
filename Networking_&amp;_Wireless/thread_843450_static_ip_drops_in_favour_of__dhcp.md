---
title: "static ip drops in favour of  dhcp"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by stratnolegs on 2008-06-28
Hey Guys
I've been experiencing a strange problem on my dapper drake server install recently.

I have my box set up with a static ip and i can connect to it fine but when i reboot my internet router (i have to do occasionally - crappy wireless) my box gets a dhcp address from the router. 
I log into the new ip, restart the network service and its back to the static one. 
This has only started recently since i came home from a lan where i had changed the network ip to automatic. I since of course changed it back but its the only recent change network related i can think of. Find below my /etc/network/interfaces

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
#changed above from static to dhcp for GLAN June 2008 (flood)
        address   192.168.1.99
        netmask   255.255.255.0
        network   192.168.1.0
        broadcast 192.168.1.255
        gateway   192.168.1.1

```

---

### Post by stratnolegs on 2008-06-30
Anyone any idea on this?
Its kinda strange and really annoying now.

---

