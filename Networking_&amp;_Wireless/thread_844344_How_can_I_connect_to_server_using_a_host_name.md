---
title: "How can I connect to server using a host name?"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by ofir_k on 2008-06-29
Hello,

I am wondering how can I use hosts names instead of IPs when connecting to a local SSH server (running on Ubuntu Hardy) through Places->"Connect to Server...".

All computers on the network are connected to a router which assigns IPs randomly (although it sometimes to assign the same IPs for the same computers).

Thanks in advance,
Ofir

---

### Post by nunki on 2008-06-29
You should be able to edit your hosts file, although if the ip's of the computer changes you would need to update the entries in this file. Perhaps someone knows a better way, but you could try this to start with.
```

gksudo gedit /etc/hosts

```

Place the ip address and the name you wish to give it.

---

### Post by Iowan on 2008-06-29
My local DNS server (which happens to be my router) has names/addresses in it's **hosts** file.

---

