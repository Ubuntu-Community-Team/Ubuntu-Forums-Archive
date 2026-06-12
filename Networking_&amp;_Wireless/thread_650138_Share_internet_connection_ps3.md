---
title: "Share internet connection ps3"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by Nergar on 2007-12-25
I have searched the forums and all i can find is post mentioning to install firestarter but I WONT DO THAT, it always crashes and doesn't work!! so please don't suggest to install firestarter.

I just bought a PS3 and i want to play online. the thing is:

nergar-pc (my pc) is connected to my wireless access point (192.168.1.254) with eth1 (192.168.1.78), it also has eth0 (192.168.2.1) with dhcp3-server running. 

So, what can i do to share my internet connection with the ps3?
The ps3 is manually configured to IP:192.168.1.10, defaut router: 192.168.2.1 and DNS: 208.67.222.222 

i tried 
```
root@nergar-pc:/home/daniel# echo "1" > /proc/sys/net/ipv4/ip_forwardroot@nergar-pc:/home/daniel# iptables -t nat -A POSTROUTING -s 192.168.2.10 -o eth1 -j MASQUERADE
root@nergar-pc:/home/daniel# iptables -I FORWARD -j ACCEPT -s 192.168.2.10root@nergar-pc:/home/daniel# 

```

Any help is appreciated!

---

### Post by specvthis on 2007-12-26
Well you need to hvae your PS3 on the same subnet as the shared nic.  If you make the ps3 192.168.2.10 you might have better luck.

---

### Post by Nergar on 2007-12-29
yes your right! lol i never noticed i had the ps3 in 192.168.1.10 instead of .2.10

well i got it working with this commands:

iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
iptables -I FORWARD -j ACCEPT -s 192.168.2.10

and its working OK i guess, but when i test the connection in the ps3, it complains about the NAT. 

It says NAT type 3, some features in online gameplay me not be available,

Anyone knows how to solve NAT problems??

---

### Post by doublez on 2007-12-29
When I had my NAT at 3, I turned on UPnP in my router and that lowered it to level 2. (You'll have to make sure it's on in your ps3 too.)

---

