---
title: "Internet not working"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Kivamaki on 2007-05-06
Just installed ubuntu and the internet isn't up. So I'm wondering how to set it up. I have a wireless router and I'm on the wireless **adapter**, not a card.

My router is a WRT54GS, made by linksys. I couldn't find any internet setup guides, I did read a Wifi one, but that didn't work for me.

---

### Post by dante.regis on 2007-05-06
what exactly is not working? Your internet or your wireless card? 

EDIT: by card, I mean adapter. And if it is the problem, which model is it?

---

### Post by Kivamaki on 2007-05-06
It's my internet, I haven't tried to setup anything because I don't know how.

---

### Post by Kivamaki on 2007-05-07
Bump.

---

### Post by dante.regis on 2007-05-07
Are there any other computers on your network? Can they access the internet? Can you "ping" them?

HOW TO PING:
First, find out the IP number of the computers. **If on windows**, go to Network Connections and on the Local Network Connection, right click and choose Status. The will be a TAB called SUPPORT. You will find the IP Address there (something like 192.168.1.3 or 10.0.0.4). **If on linux, **, go to the terminal and type 
```
ifconfig | grep inet
```. Ignore any address like 127.0.0.1, 0.0.0.0 or 169.254.x.x

Now, either on linux or windows, go to a terminal (or command prompt) and type
```
ping xxx.xxx.xxx.xxx
``` filling the X's with the ip addresses you found.

---

### Post by Kivamaki on 2007-05-07
Yeah..I already know my IPs. So what do I do with them in Linux.

---

### Post by dante.regis on 2007-05-07
we need to isolate the problem. that's why I asked if the other computers on your network can access the internet. can they? Also, you didn't told us if you can ping the other computers.

Try issuing a 
```
ping xxx.xxx.xxx.xxx
``` and see if you have something like this as a result:
```

64 bytes from xxxxxxxxxx: icmp_seq=1 ttl=64 time=14.1 ms
64 bytes from xxxxxxxxxx: icmp_seq=2 ttl=64 time=18.8 ms
64 bytes from xxxxxxxxxx: icmp_seq=3 ttl=64 time=14.5 ms
64 bytes from xxxxxxxxxx: icmp_seq=4 ttl=64 time=14.8 ms
64 bytes from xxxxxxxxxx: icmp_seq=5 ttl=64 time=19.8 ms

```

Best,
Dante

---

