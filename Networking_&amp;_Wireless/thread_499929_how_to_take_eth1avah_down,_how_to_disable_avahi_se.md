---
title: "how to take eth1:avah down, how to disable avahi service"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by iler61 on 2007-07-13
1. How do I remove the eth1:avah interface ? 'ifconfig eth1:avah down'
gives me error (SIOCSIFFLAGS: Cannot assign requested address)

2. How do I disable the the avahi forever ? It is disabled in sysv-rc-conf, but
it starts ? Is it started by some other service ? How do I disable it ?

Yakov

---

### Post by spd106 on 2007-07-13
1. You can't use ifdown because it reads the interfaces file for names and eth1:avahi isn't listed there, it's really more of a temporary hack. Use this instead.
```
sudo ifconfig eth1:avahi down
```

2. To disable Avahi, take the avahi-daemon down by issuing
```
sudo /etc/init.d/avahi-daemon stop
```

To prevent Avahi running automatically on start-up modify the /etc/default/avahi-daemon file or untick service discovery in the network-admin capplet (System -> Admin -> Networks).

---

### Post by ariel on 2008-01-15
In gutsy, you can disable avahi by doing System > Admin > Services  and disabling "Multicast DNS service discovery"

---

### Post by Natume on 2008-04-04
I don't know if this will be of use to anybody, but I stumbled upon a solution that seems to work.  Precisely how it does it's magic (what it disables) I'm not sure, since it utilized the gui network manager (System -> Administration -> Network).

On Feisty, turning of DNS Multicast Detection doesn't prevent avahi-autoipd from popping up, and in my case fiddling with VPN in a bad way, despite disabling the avahi daemon.  However, if you go to System -> Administration -> Network (there's probably an equivalent way to do it in the terminal, but I haven't bothered looking), chances are one or both of the wireless / wired network interfaces are going to be in DHCP mode.  Change both of them to roaming mode, and avahi-autoipd stops popping up.  (Consequently, the virtual interface, ethX:avahi, doesn't get bound.)

If this completely solves my VPN problems, I'm not sure, but it's a start.  Hopefully this helps for those that are wondering how to get rid of avahi-autoipd for whatever reason.

~Natume

---

