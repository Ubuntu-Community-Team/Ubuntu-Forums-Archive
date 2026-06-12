---
title: "Dual Networks usage"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by ranpha on 2006-08-30
Can you use two networks at the same time in Ubuntu?

I don't mean a firewall etc or internet sharing. I want one computer that can acces two different networks (wired and wireless) at the same time

---

### Post by spd106 on 2006-08-30
Sure, why not?

Just be aware that it is best to have only one default route. Check **ip route** or **route**. If you have two then there will be a conflict and you may have an intermittant connection at best. Use **sudo ip route del** to remove one of them.

For extra fun you can even have a wireless adaptor connect to multiple APs at the same time, if your hardware supports it.

---

### Post by ranpha on 2006-08-31
si it's the same as in winblows... there i had two network cards one on dhcp and one static without a gateway then all internet went over de dhcp and samba went over de static....but how can i do this with networkmanager??? there everthing is dhcp

---

### Post by spd106 on 2006-08-31
Network Manager will ignore and interfaces configured in the **/etc/network/interfaces** file. Assuming you have eth0 using dhcp and eth1 as a static interface. The file should have lines that look like these:

```
iface eth1 inet static
address 192.168.0.1  <-- change this
netmask 255.255.255.0

auto eth1
```

It may also be possible to have this on dhcp as well and have a post-up line that removes the gateway given by the dhcp server. I'm not sure about this though. Have a look at **man interfaces** for more details.

---

### Post by ranpha on 2006-09-01
thanks i got a idea now....thanks for the input will do something after i come back from the states

---

