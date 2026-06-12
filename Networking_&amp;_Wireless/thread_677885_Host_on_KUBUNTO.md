---
title: "Host on KUBUNTO"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by tchayya on 2008-01-25
I were using a virtual machine on witch i have ubunto, i gave it a host name, & i was access on it from my internal network by using [http://tchaya/](http://tchaya/), now i install Kubunto on an other pc & i give it a host name (tchayya) but i could not acces it using [http://tchayya/](http://tchayya/) but i can access it by entering its IP address, how can i access it by calling its name?
Regards :confused:

---

### Post by fs3rp4 on 2008-01-25
> **tchayya said:**
> I were using a virtual machine on witch i have ubunto, i gave it a host name, & i was access on it from my internal network by using [http://tchaya/](http://tchaya/), now i install Kubunto on an other pc & i give it a host name (tchayya) but i could not acces it using [http://tchayya/](http://tchayya/) but i can access it by entering its IP address, how can i access it by calling its name?
Regards :confused:

Hi

Execute this command:

sudo gedit /etc/hosts

Insert this after the localhost line

"IP NUMBER" tchaya


save

---

