---
title: "fail to start bind"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by kroiz on 2007-10-21
Howdy,
I am trying to set up bind9 master name server on my computer.
I followed the [instruction]("https://help.ubuntu.com/community/BIND9ServerHowto") on the ubuntu wiki ( I did not do the part about chrooting cause I think It is not mandatory for bind to work. right?) 

but when I try to start the process
```
 sudo /etc/init.d/bind9 start
 * Starting domain name service... bind                                  [fail] 

```I get the following error in my logs
```
kernel: [ 6467.908126] Failure registering capabilities with primary security module.
```

anyone stumble upon this?

---

### Post by kroiz on 2007-10-28
does anybody has a LAN which he can ping in a terminal a computer by name?
if you do.
did you use bind?
or some other simpler program?

---

### Post by Felarin on 2007-11-01
I have the same issue in Gutsy. Any idea how to fix this?

---

### Post by kroiz on 2007-11-02
> **Felarin said:**
> I have the same issue in Gutsy. Any idea how to fix this?

There is a simpler program:
dsnmasq
I will try it out soon.

---

### Post by pmilano1 on 2007-12-11
Anyone figure out why this happens?

---

### Post by kroiz on 2007-12-11
nah I gave up.

---

