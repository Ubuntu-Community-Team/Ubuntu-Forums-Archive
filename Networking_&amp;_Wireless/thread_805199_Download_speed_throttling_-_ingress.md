---
title: "Download speed throttling - ingress"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by rampageoberon on 2008-05-23
Hi,

I'm having trouble throttling my download speeds. I am trying to set up a different throttle for the LAN and a different throttle for general internet use.

Here is the code I'm using.

/sbin/iptables -t mangle -I PREROUTING 1 -m iprange --src-range 192.168.0.0-192.168.100.100 -j MARK --set-mark 1
/sbin/iptables -t mangle -I PREROUTING 2 -m iprange ! --src-range 192.168.0.0-192.168.100.100 -j MARK --set-mark 2

/sbin/tc qdisc add dev eth0 handle ffff: ingress
/sbin/tc filter add dev eth0 parent ffff: protocol ip handle 1 fw police rate 90mbit burst 1m drop
/sbin/tc filter add dev eth0 parent ffff: protocol ip handle 2 fw police rate 1mbit burst 10k drop

Not sure why this doesn't work. I can do a general throttle using u32 and matching dst ip but I need 2 throttles.

Thanks

---

### Post by rampageoberon on 2008-05-27
Anyone able to help with this please?

---

### Post by rampageoberon on 2008-06-02
I'm guessing thats a not then :(

---

### Post by Boozkachu on 2008-12-17
Have you checked out trickle?
```
sudo apt-get install trickle
```

Also check out:
[http://www.mastershaper.org]("http://www.mastershaper.org")
and
[http://lartc.org/]("http://lartc.org/")

Hope you find a solution.

---

### Post by rampageoberon on 2008-12-17
Hi,

Thanks for the suggestions. Trickle looks quite good, is it possible for it to limit by IP though as I would like 2 separate download limits, one for the local network and one for the external network.

I have had a read through lartc.org and thats where I got the code in my first post from. I have something similar which does uploads very well.

MasterShaper looks interesting, unfortunately I don't know how to patch a kernel and have never ventured there.

Are there any good guides that you could point me to?

Also does the code in my first post look reasonable or is it flowed? I put it together from examples and documentation on lartc.org.

many thanks

---

