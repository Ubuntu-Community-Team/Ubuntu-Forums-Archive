---
title: "Network interface"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by halon on 2008-01-02
I have a Dell Inspiron 6000 with Intel wireless card running Ubuntu 7.04.  Is there a way to make eth0 my default interface so that the wireless will not be active until ifup eth1??

---

### Post by sdide on 2008-01-02
in /etc/network/interfaces
remove the line 

auto eth1

---

### Post by Predator[23rd] on 2008-01-02
Hi!

yes, it is possible. just remove the "auto" from your */etc/network/interfaces* file for eth1.

---

### Post by halon on 2008-01-02
Thank you both, that worked :)

---

