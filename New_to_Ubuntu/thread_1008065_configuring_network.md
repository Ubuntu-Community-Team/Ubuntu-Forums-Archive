---
title: "configuring network"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-11
I just installed Ubuntu 8.10 server to use as a file server on my local network. DHCP on my linksys router does not seem to like ubuntu so I set up my network config manually during the install. Problem is I still don't connect to internet to get updates. I want to look at my network config so I can make sure everything is rite. Problem is I don't know how. How do I look at my network config on ubuntu 8.10 server? thanks

---

### Post by Michael.Godawski on 2008-12-11
I am a server novice, so I will just point you in one direction:


[LIST]
[*][https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html)
[*][http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)
[/LIST]

---

### Post by hyper_ch on 2008-12-11
what's the output of
```

cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig

```

---

### Post by pshootr on 2008-12-11
> **hyper_ch said:**
> what's the output of
```

cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig

```

cat /etc/network/interfaces "works. Thanks"

cat /etc/resolv.conf "says no such file exists" guess cuz dhcp failed during install I have not learned how to enter dns yet.

ifconfig "worked thank you"

---

### Post by hyper_ch on 2008-12-11
I need the output. and enclose it in [noparse]```

```[/noparse] brackets.

---

