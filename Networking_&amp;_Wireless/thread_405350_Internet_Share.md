---
title: "Internet Share"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by lil_barba on 2007-04-09
i have a pppoe internet (dynamic IP) connection and i want to share it from ubuntu 6.10 to windwos xp
i tried firestarter but it didn't work
i need a noob tutorial :)
thank you 
barba

---

### Post by mssever on 2007-04-10
The easiest thing is to use a hardware router.

If you use your Linux box to do the routing, you'll likely need to use a crossover cable between your machines.

I don't know anything about the actual routing software to use, because I use a hardware router that works great for me (Linksys WRT54G).

---

### Post by lil_barba on 2007-04-10
> **mssever said:**
> The easiest thing is to use a hardware router.

If you use your Linux box to do the routing, you'll likely need to use a crossover cable between your machines.

I don't know anything about the actual routing software to use, because I use a hardware router that works great for me (Linksys WRT54G).

i have a router but it restrains my speed. and i need full speed on one of my computers and internet on the other one :)
on the linux machine i have 2 netowrk cards (eth0 and eth1) and everything is connected i just have to do the software :)

---

### Post by lil_barba on 2007-04-15
i really need some help :D

---

### Post by AnRa on 2007-04-15
A very simple way to do it is:

**Ubuntu box**

1.- Open a console window
2.- Type
```
sudo -i
iptables -t nat -A POSTROUTING -o [COLOR="Red"]ppp0[/COLOR] -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
exit
```

**Windows XP box**
1.- Set the gateway IP equal to Ubuntu box's IP

---

