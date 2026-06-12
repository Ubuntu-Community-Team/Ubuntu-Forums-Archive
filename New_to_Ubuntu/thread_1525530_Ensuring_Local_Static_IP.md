---
title: "Ensuring Local Static IP"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-06
I'm trying to set up a local static IP on my laptop. I was using System | Preferences | Network Connections to ensure that the IP was static. However, this was causing problems with SSH. So instead, I modified /etc/network/interfaces. The file is pasted below:

```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0
broadcast 192.168.1.255

```

(I haven't set up my wireless connection yet).

My question is will my IP be static even though in Network Connections auto eth0 is set to DHCP?

---

### Post by Iowan on 2010-07-06
Network Manager is evolving. In previous versions, */etc/network/interfaces* would override Network Manager - I'm not sure that's true any more.  
If you have access to the DHCP server, another option is to create a static *lease* based on MAC address. End result is the same - the machine always gets the same address, but machine can remain set up for DHCP... especially useful if machine moves between networks.

---

### Post by EnigmaticCoder on 2010-07-07
As a matter of fact, I set up a static lease on my router. The only problem is that the IPs distributed didn't match with the lease! So I tried to also set up static IPs on the machines, but then I got the headaches with SSH. Fortunately, I can keep a static IP on the server and have a dynamic IP on the client and SSH will work that way. Since this solution is available, I'm going to call it a night and mark this thread as solved. Thanks for your input.

---

