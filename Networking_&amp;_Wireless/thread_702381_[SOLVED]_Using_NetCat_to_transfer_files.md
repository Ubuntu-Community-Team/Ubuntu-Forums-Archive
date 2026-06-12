---
title: "[SOLVED] Using NetCat to transfer files"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Darkade on 2008-02-20
Hello, I'm trying to use NetCat to transfer some files in my local network. The thing is that netcat seems not being opening ports. I mean when I

```
$ nc -l 3333
```

in my computer netcat seems to be listening to port 3333. But when from another computer I do

```
$ nc this_machine's_ip 3333
```

I get some conection refused error, saying that the port ain't available.

(UNKNOWN) [this_machine's_ip] 3333 (?) : Connection refused

The ip is right since when I ping it it says the machine was found. I've also try to 'port forward' port 3333 to this machine but that wouldn't work neither.

So, how can I make nc listen on that port? or is it that such port is blocked? or am I using nc in the wrong way?
thanks :lolflag:

---

### Post by ruy_lopez on 2008-02-20
Have you tried specifying the listening port with:

```
nc -l -p 3333
```

Then connect with:

```
nc address 3333
```

---

### Post by Darkade on 2008-02-20
> **ruy_lopez said:**
> Have you tried specifying the listening port with:

```
nc -l -p 3333
```

Then connect with:

```
nc address 3333
```

Hehe. So simple. :D:D Thanks for the quick answer. It's seems to be working fine :lolflag:

---

