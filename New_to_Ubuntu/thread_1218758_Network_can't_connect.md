---
title: "Network can't connect"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by naisho on 2009-07-21
Hi! I just installed jaunty on my external HDD. I have a wired connection and accordingly put the proper addresses in the fields. Saved it and still it says auto eth0 connection failed.
Logged out, rebooted and still the same issue. It starts by saying "Settings network addresses" and afterawhile same error "connection to network failed". Please help! My network works through Arch and windows installed in my internal HDDs.

---

### Post by superprash2003 on 2009-07-21
did you add the ip info using network manager? post output of **ifconfig** from the terminal

---

### Post by bacil on 2009-07-21
Can you also send us content of /etc/network/interfaces

---

### Post by naisho on 2009-07-21
> **bacil said:**
> Can you also send us content of /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

And my ifconfig is as it supposed to be. I don't think there's any need for that. Any ways, the main question is where is /etc/rc.conf or resolv.conf ?? How can I set up my IP/DNS manually?? Since using the KNetwork manager isn't working.

---

### Post by naisho on 2009-07-21
Err..I just founf out that I don't have a resolv.conf file in /etc

Any ideas?

---

### Post by ~sHyLoCk~ on 2009-07-21
Create your own /etc/resolv.conf file and add the nameservers and it should work.
Also make sure your IP add and gateway and dhcp/Static is added in /etc/network/interfaces

---

