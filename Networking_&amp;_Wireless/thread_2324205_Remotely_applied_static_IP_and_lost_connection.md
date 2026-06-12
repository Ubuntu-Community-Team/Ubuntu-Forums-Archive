---
title: "Remotely applied static IP and lost connection"
date: 2016-05-11
forum: Networking &amp; Wireless
---

### Post by lynx6492 on 2016-05-11
I know, I'm a genius right :-/  

I am using some tunneling software to connect a ubuntu server in a data center to a ubuntu server with a local private IP at one of our offices.  I am going to the site tomorrow so I should be able to recover from my error but just wondering if anyone can help me out to see where I went wrong.  I amended the interface file with the below info, this is all the correct IP information but then I lost the connection, the tunnel is scripted to reestablish itself every 30 seconds so it's not a problem with the tunnel and had been working regardless of my IP before.  Thanks for any help in advance, at the very least I'm hoping to see what I can do when on site to correctly apply the static private IP with internet access.

# The primary network interface
    auto ens32
    iface ens32 inet static
    address 10.0.0.35 
    netmask 255.255.255.0
    gateway 10.0.0.1 
    up route add default gw 10.0.0.1 dev ens32

---

