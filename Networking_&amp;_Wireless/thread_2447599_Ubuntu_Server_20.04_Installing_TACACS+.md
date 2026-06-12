---
title: "Ubuntu Server 20.04 Installing TACACS+"
date: 2020-07-22
forum: Networking &amp; Wireless
---

### Post by coconutdog2 on 2020-07-22
Hi all,

Does anyone know the command to install TACACS+ on Ubuntu Server 20.04? Most sites suggest to use

```
apt-get install tacacs+
```

This does not work, I get the following:

```
root@optplex-780:/etc# apt-get install tacacs+
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tacacs
root@optplex-780:/etc#
```

Computer has access to the internet and I've refreshed the apt package lists.

Cheers.

---

