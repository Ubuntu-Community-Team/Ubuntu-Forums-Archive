---
title: "No eth0?"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by jwalker on 2007-06-10
Hi all

I'm running Fiesty (though this same issue happened in Dapper) on a (notebook) Dell Latitude D600 (the main factor here I think), and sometimes but not always, I will boot up and not have a eth0 interface. My wireless will be there (eth1) but not my wired network card. 

Running ifconfig will show only eth1 and the loopback. 

Rebooting may or may not fix the issue, as of right now, almost a dozen reboots has done nothing.

So temperamental! Sometimes it will work without a single issue (barring wireless - :-P) and other times it is a very poorly behaved comp. 

Anyway, has anybody seen this issue before?

Thanks

Chris

---

### Post by NeoLithium on 2007-06-10
Can you copy and paste the output of this command from terminal?
```
cat /etc/network/interfaces
```

---

### Post by jwalker on 2007-06-10
Can't really copy and paste (no network connectivity on bad computer) but the following interfaces are listed in the format:

auto xxx
iface xxx inet dhcp

lo
eth0
eth1
eth2
ath0
wlan0

Thanks

Chris

---

### Post by jwalker on 2007-06-10
You see! I turned the laptop off for 20 mins, turned it back on, and this time eth0 was detected and loaded up fine. 

SERIOUSLY WTF?!! 

I love the Kubuntu Feisty but sometimes, sometimes I do consider installing Windows instead, just so retarded stuff like this didn't happen. I work in IT and the amount of faffing around on the networking side of things is really, really letting this project down for me. There is no way I could get any of my mates onto Ubuntu. A shame too, because its easy to see what great efforts have been made by people for the sake of Ubuntu. 

Good luck all, and one favour to ask. For all of those who have notebook/laptops and do not have any issues whatsoever, perhaps it would be nice if you could mention your model, a sticky or something would be good. 

kthxbye

---

