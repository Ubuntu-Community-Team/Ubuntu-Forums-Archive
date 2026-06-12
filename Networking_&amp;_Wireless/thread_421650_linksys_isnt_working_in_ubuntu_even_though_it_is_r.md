---
title: "linksys isnt working in ubuntu even though it is reconized"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by jaygriffen06 on 2007-04-24
I am using a linksys wireless card, i dual boot ubuntu, windows. works fine in windows but in ubuntu it will read the wireless card give me a list of router, i set everything to the routers settings, but i click connect it will take a wile for it to say its connected but im not realy connected i have tryed pinging the router but it says unreachable.

---

### Post by bnuytten on 2007-04-24
Please post output of
```

cat /etc/network/interfaces
iwconfig
ifconfig

```

---

### Post by jaygriffen06 on 2007-04-24
> **bnuytten said:**
> Please post output of
```

cat /etc/network/interfaces
iwconfig
ifconfig

```

do i type that into the terminal? whats that code for?

---

### Post by bnuytten on 2007-04-24
Yes you type it in a terminal. Do not mind the "Code:" thing. It is some kind of unwritten forum rule to put things that belong "outside" the normal text between CODE quotes.

---

### Post by jaygriffen06 on 2007-04-24
> **bnuytten said:**
> Yes you type it in a terminal. Do not mind the "Code:" thing. It is some kind of unwritten forum rule to put things that belong "outside" the normal text between CODE quotes.

it will show the status of all internet connections, but what am i looking for.

---

### Post by bnuytten on 2007-04-26
> **jaygriffen06 said:**
> it will show the status of all internet connections, but what am i looking for.
You'd be looking for a missing/incorrect IP address, missing routes, not associated with an Access Point, ... There are many things. If you post the output here, we will be able to get a clear view on your situation. It's impossible to say what the solution is if we haven't pinpoint the cause. And to pinpoint the cause, we need to know the situation :-)

---

