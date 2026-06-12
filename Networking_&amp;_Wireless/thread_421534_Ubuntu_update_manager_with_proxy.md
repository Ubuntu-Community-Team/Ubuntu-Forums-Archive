---
title: "Ubuntu update manager with proxy"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by jefh262 on 2007-04-24
I am at school with my computer installed with ubuntu edgy, however, i can not figure out how to get the update manager to work with the school internet.
The proxy is 'proxy2'
The port is '8080'
And to log into the internet in firefox a box comes up saying:
'Enter username and password for proxy "" at proxy2:8080'
my username is computing\joebloggs
computing is the domain
Please help, i am fairly new to linux so don't make it too complex though.
Thanks

---

### Post by solar george on 2007-04-24
There are proxy options (under the networking tab) in the preferences of synaptic.

---

### Post by jefh262 on 2007-04-24
I have tried that but it does not have password options and domain options. i have tried just entering the proxy and port but it does not work.

---

### Post by solar george on 2007-04-24
Click on the 'authentication' button on the proxy option page.

---

### Post by jefh262 on 2007-04-24
I can't find that on synaptic so i assume that you are talking about network proxy; i have done this but it still does not seem to work!

---

### Post by solar george on 2007-04-24
> I can't find that on synaptic so i assume that you are talking about network proxy; i have done this but it still does not seem to work!

It is on the network options tab of the synaptic preferences.

---

### Post by jefh262 on 2007-04-24
not there for me! However, when configuring that proxy in kde (my 2nd desktop browser), it recognises the proxy and changes proxy2 to proxy2.computing.local, I have tried this but it still does not work. The internet works on firefox but not on the desktop at startup, even if i set the proxy under network proxy.

---

### Post by solar george on 2007-04-24
Open a terminal and type,
```
ping bbc.co.uk
```

You should be a scrolling list, like
```
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=1 ttl=119 time=249 ms
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=2 ttl=119 time=22.1 ms

```
(press ctrl+c to stop it)

If you get that try
```
telnet www.bbc.co.uk 80

```

if you can connect you should get
```
Trying 212.58.224.83...
Connected to www.bbc.net.uk.
Escape character is '^]'.

```

Post what happens.

---

### Post by sonofanickel on 2008-01-29
thanks for the tip about network settings in synaptic package manger. This allowed me to input my proxy information in order to update my system using the update manager after a fresh install.

---

