---
title: "hosts by name impossible?"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by gratefulfrog on 2008-04-04
I have a network with a router a Ubuntu pc and a Win XP pc.

I can ping only IP addresses, but cannot ping hosts by name.

Can anyone tell me how to make that work?
Thanks,
GF

---

### Post by Cannaregio on 2008-04-04
I wonder... could you please try the traceroute+ping [mtr]("http://www.bitwizard.nl/mtr/") ([COLOR="Blue"]sudo apt-get install mtr[/COLOR]) and use 
the "n" key to switch?
Does it switch between DNS-names and IPs?
Does it work "outside" ([COLOR="Blue"]sudo mtr google.com[/COLOR])?

---

### Post by gratefulfrog on 2008-04-04
Thanks for your quick reply
mtr with an IP address is ok
mtr with a local network host name fails, even for the host from which it is run
mtr google.com is ok.

mtr -n means do not use DNS. I don't think I have DNS on my local network, but how can I tell?

Have we made progress?
Cheers,
GF.

---

### Post by chili555 on 2008-04-04
The quick-n-dirty way to do it is to associate the names with the numbers in /etc/hosts by adding a couple of lines:```
computer's_name 192.168.1.103
computer2 192.168.1.105
```Then you can do:```
 ping -c3 computer2
PING 192.168.1.103 (192.168.1.103) 56(84) bytes of data.
64 bytes from 192.168.1.103: icmp_seq=1 ttl=64 time=59.3 ms
64 bytes from 192.168.1.103: icmp_seq=2 ttl=64 time=3.89 ms
64 bytes from 192.168.1.103: icmp_seq=3 ttl=64 time=3.44 ms

--- 192.168.1.103 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 3.442/22.228/59.346/26.247 ms
```Note that you must then use static IP addresses. Yes, XP has a 'hosts' file, too.

Not sure I understand how *mtr* can help here, but I am anxious to be enlightened.

The not so quick option is BIND. Check it out with the search function here.

---

### Post by Cannaregio on 2008-04-04
> **chili555 said:**
> Not sure I understand how *mtr* can help here, but I am anxious to be enlightened.

Well, I thought he could subsequently try mtr (which is a PING+traceroute appz) in order to test whether the DNS servers are running by pinging their IP addresses.

Maybe trying a telnet session on port 53 of the DNS server? If it works, the DNS service is working. If the DNS service runs, then query the DNS with nslookup.

Methinks that if  pinging hostnames fails and the IP address ping succeeds, the problem is probably name resolution.

> **gratefulfrog said:**
> mtr -n means do not use DNS. I don't think I have DNS on my local network, but how can I tell?

No, not [COLOR="Blue"]mtr -n[/COLOR]... just clicking the "n" key (which is a toggle) once -say- [COLOR="#0000ff"]mtr google.com[/COLOR] or [COLOR="Blue"]mtr 64.233.167.99[/COLOR] are running.

---

### Post by Eiríkr on 2008-04-04
Name resolution via NetBIOS (the default Windows way of networking) works a bit wonkily in XP, from what I've read, such that a network of WinXP shares and Ubuntu clients will consistently fail to resolve WinXP hostnames from the Ubuntu machines.  I'd recommend the quick-and-dirty /etc/hosts file approach suggested by chili555.  :)

Cheers,

Eiríkr

---

### Post by gratefulfrog on 2008-04-05
Thanks for the replies! I've gone the /etc/hosts route and that's good enough for me.

I'm still hoping to see the content of the windows shared floders, one day, though. (see my other thread: 
[http://ubuntuforums.org/showthread.php?t=745405]("http://ubuntuforums.org/showthread.php?t=745405")

Ciao,
GF.

---

