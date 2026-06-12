---
title: "can iptables do both udp and tcp on nat?"
date: 2023-02-03
forum: Networking &amp; Wireless
---

### Post by ulao3 on 2023-02-03
I'm trying to satisfy this

Forward the ports manually by changing the settings in your router.                              You need to forward port **8788 for TCP** traffic                              and port **8781 for TCP and UDP** traffic.


I want this 
iptables -t nat -A PREROUTING -i enp0s2 -p udp,tcp --dport 8781 -j DNAT --to-destination 192.168.0.07:8781
iptables -t nat -A PREROUTING -i enp0s2 -p tcp --dport 8788 -j DNAT --to-destination 192.168.0.07:8788

but the comma is not legal. How can I use udp and tcp on 8781?

---

### Post by The Cog on 2023-02-04
Maybe with a separate line for each?
```
iptables -t nat -A PREROUTING -i enp0s2 -p tcp --dport 8081 -j DNAT --to-destination 192.168.0.07:8781
iptables -t nat -A PREROUTING -i enp0s2 -p udp --dport 8081 -j DNAT --to-destination 192.168.0.07:8781
iptables -t nat -A PREROUTING -i enp0s2 -p tcp --dport 8888 -j DNAT --to-destination 192.168.0.07:8788
```
Or 8781 and 8788 if they're the numbers you want. Your post seems a little confused on port numbers. 
I couldn't find a way to combine the lines.

---

### Post by ulao3 on 2023-02-04
ah fixed that error... but I thought multi lines overwrote the former?

---

### Post by Doug S on 2023-02-04
> **ulao3 said:**
> ah fixed that error... but I thought multi lines overwrote the former?No, you are using "Append", -A. From the man page:

```
       -A, --append chain rule-specification
              Append one or more rules to the end of the selected chain.  When the source and/or destination names resolve to more than one address, a rule will be added for each possible address combination.
```

---

### Post by ulao3 on 2023-02-04
well damn, still not working... 

iptables -t nat -A PREROUTING -i enp0s2 -p tcp --dport 8781 -j DNAT --to-destination 192.168.0.07:8781
iptables -t nat -A PREROUTING -i enp0s2 -p udp --dport 8781 -j DNAT --to-destination 192.168.0.07:8781
iptables -t nat -A PREROUTING -i enp0s2 -p tcp --dport 8788 -j DNAT --to-destination 192.168.0.07:8788

---

### Post by SeijiSensei on 2023-02-04
Try removing the leading zero in 192.168.0.07 so it reads just 192.168.0.7.

---

### Post by The Cog on 2023-02-04
And use **iptables-save -c** to print the current rules and the hit counters. Looking at that may help.

---

### Post by ulao3 on 2023-02-05
yeah its appending it for sure, hmmm.  Also removed the zero. Maybe its some crap on the target system, ill snif the wire. Thx for the help.

---

### Post by ulao3 on 2023-02-05
crap I forgot I use ufw now... Not sure there is much different but its just 

 ufw  allow 8788
 ufw  allow 8781


right? UDP and tcp are both added? Isn't ufw just a fancy iptables?

---

### Post by Doug S on 2023-02-05
No, for my understanding of what you are trying to do, the UFW rules would be more complicated than that.
Yes, UFW is just a front end for itpables.

I do not like UFW, and do not use it. I also find the UFW generated iptables rules sets difficult to read, understand, and follow.

---

### Post by The Cog on 2023-02-06
> I also find the UFW generated iptables rules sets difficult to read, understand, and follow.
Convoluted and labyrinthine are words I might use for the iptables rules that ufw generates. I don't use it (actually I don't use iptables either, I use nftables).
However, ufw does remember to add rules that allow in and out of the loopback interface to that inter-process communication works. Lots of people making manual iptables rules forget that bit.

---

