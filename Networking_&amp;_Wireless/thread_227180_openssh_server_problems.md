---
title: "openssh server problems"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by nismohasan on 2006-08-01
i can connect via localhost so i know that the server is setup correctly however if i try to connect from outside the box via a dns redirect hostname it doesn't allow me to connect 

> ssh: connect to host *****.gotdns.org port 22: Connection refused.

ive got a static ip but have setup the routers dns client and so on, can access the web interface of the router trhough the hostname.

i've forwarded port 22 on my router (192.168.1.1) to this box (192.168.1.6) and opened port 22 with firestarter but still no luck?

can anyone help me out here?

---

### Post by rbalfour on 2006-08-01
have you tried with the ip address?

---

### Post by nismohasan on 2006-08-01
> **rbalfour said:**
> have you tried with the ip address?

i have same thing happens as with the hostname.

canyouseeme.org lists port 22 as being closed so i've opened port 6666 on my router, configured the ssh server to use port 6666 instead of 22 but i still can only connect via localhost

canyouseeme.org can see that port 6666 is open

> hasan@nismo-oobuntoo:~$ ssh [email]hasan@*****.gotdns.org[/email]
ssh: connect to host *****.gotdns.org port 6666: Connection refused

---

### Post by nismohasan on 2006-08-02
nvm problem solved

---

### Post by Hatchetfish on 2006-08-31
Can you explain how you solved it?  I'm facing the exact same situation, and have no idea. (other than 22 is reported open by canyouseeme, so I'm sticking with it.)

---

