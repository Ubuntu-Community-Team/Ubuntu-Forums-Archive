---
title: "Static IP, Local Network, Dual Network Cards Help"
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by r541678 on 2017-11-18
I have a ubuntu machine with 2 network cards, I have enabled ip routing but cant seem to get my local network to communicate to internet, i can ping between networks and the ubuntu machine has static Ip and is communicating on internet, I am posting my routing table as well as network info, any help would be appreciated.   Thanks!

my routes are:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default             rrcs-162-155-9- 0.0.0.0              UG    0      0        0 enp2s0
162.155.9.80    *                     255.255.255.252 U     100    0        0 enp2s0
link-local          *                     255.255.0.0        U     1000   0        0 enp2s0
192.168.1.0      *                     255.255.255.0    U     100    0        0 enp4s0



How do i add a route from my local 192 network to the internet so i get world access on my local network machines, currently i have internet on my ubuntu machine.

---

### Post by SeijiSensei on 2017-11-19
You need to enable masquerading.  Try running this command:
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

Replace "eth0" with the Internet-facing interface name if it is different.

If this works, you can add that command, without the "sudo", to the file /etc/rc.local which is run at each boot.

---

