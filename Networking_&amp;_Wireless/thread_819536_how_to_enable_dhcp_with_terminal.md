---
title: "how to enable dhcp with terminal"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by eru777 on 2008-06-05
hi all , how do i enable dhcp becuz when i updated drivers i lost internet connection : <
thanks
hardy heron wubi user latest

---

### Post by gradedcheese on 2008-06-05
```
sudo dhclient eth0
```

where 'eth0' can be whatever interface you're using.

---

### Post by Paul1944 on 2010-09-22
I did a   sudo dhclient eth0
It said:
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 0
....then interval 16, 11, 10, 11, 5
....then No DHCPOFFERS received.
....No working leases in persistent database - sleeping.
ifconfig - looks the same
ping still gets  unknown host
p. s.  My ethernet cable is pluged into network-1
....I also have a network-2 and an ILO

---

### Post by Paul1944 on 2010-09-22
My BAD - I feel soooooo stupid...
I KNOW to check 'everything' before posting - I had the ethernet cable plugged into the wrong port on the router... DUH !!!!!
So Sorry - I won't _ever_ post again (Not) -but- I promise to be MUCH more careful before posting in the future...
Sorry again,
Paul
:mad:
Thanks for everyone's help...

---

### Post by Jesua on 2012-06-18
> **gradedcheese said:**
> ```
sudo dhclient eth0
```

where 'eth0' can be whatever interface you're using.

It works... thanks...

---

