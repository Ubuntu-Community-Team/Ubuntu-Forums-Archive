---
title: "No Internet connection"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Skorzen on 2009-04-26
Hello.

I never had problems with my network card since some weeks ago as I got out of Internet, and I still don't understand what happened.

This is not happening just in Ubuntu or its variants, but in every distribution I install. It's annoying.

```
more /etc/network/interfaces
```
```
auto lo
iface lo inet loopback
```
--
```
lspci | grep net
```
```
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
```
--
```
more /etc/networks
```
```
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0
```

As you can deduce, if I run 'ifconfig', no ethX interfaces are listed.

Can someone please help me with this?

Thanks!

---

### Post by pbpersson on 2009-04-26
Have you tried installing a different network card?

---

### Post by cariboo on 2009-04-26
Could you open a terminal and type:

```
sudo lshw -C netwotk
```

and paste the output in your next post.

---

