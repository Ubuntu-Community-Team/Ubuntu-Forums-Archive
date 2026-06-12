---
title: "Howto Connect to P2P network"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by perito on 2008-03-25
First I changed my IP to static IP using this method
```
sudo nano /etc/network/interfaces
auto eth1
iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
sudo /etc/init.d/networking restart

```

but after that I cant connect to any network, I dont see the network in the Wireless Networks and if I typed its name in Connect to other wireless networks, it sees it but never connects (I guess its trying to acquire an ip address)

If I go to manual configuration, and I manually remove roaming and put a static IP address.. well it never happens, as soon as I close the manual configuration, it returns to roaming without a static IP address...
what should I do?
Im trying to connect to a wireless P2P network to play a game...

---

### Post by prshah on 2008-03-25
> **perito said:**
> 
but after that I cant connect to any network, I dont see the network in the Wireless Networks and if I typed its name in Connect to other wireless networks, it sees it but never connects (I guess its trying to acquire an ip address)


After editing your /etc/network/interfaces, try bringing your wireless interface up with ```
sudo ifup eth1
sudo iwconfig essid whatever
```

Also sometimes stopping and starting the network interface works better than restart (I know it shouldn't work like that but experience says otherwise...)

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

also ```
dmesg | tail -10
``` will save you a lot of guesswork.

---

