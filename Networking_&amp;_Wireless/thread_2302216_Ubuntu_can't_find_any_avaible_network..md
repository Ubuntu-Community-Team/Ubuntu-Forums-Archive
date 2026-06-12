---
title: "Ubuntu can't find any avaible network."
date: 2015-11-08
forum: Networking &amp; Wireless
---

### Post by Adrian_Oneasca on 2015-11-08
Greetings, some days ago I got a dedicated server from OVH, today I installed the Ubuntu 14.04 server iso on it.
During the install process the install manager warned me it couldn't find any network interfaces, I didn't put much attention into it at that time, after the installation finished I don't have any network on my system, a output if "ifconfig":
[IMG]https://i.gyazo.com/28aa4ead324f18083c5fed3d770ee8ba.png[/IMG]

---

### Post by matt_symes on 2015-11-08
Hi

There are no network interfaces at all ? This will show us hardware Ubuntu thinks you have (capital C below)

```
sudo lshw -C network
```

and 

```
lspci
```

...or are the interfaces just down ?

```
ifconfig -a
```

Do you know what hardware the server actually has ?

Please provide more information about the server itself.

Kind regards

---

### Post by Adrian_Oneasca on 2015-11-09
[IMG]https://i.gyazo.com/0267a88dc7ac00c3774979d1ecaa2ee2.png[/IMG]
[IMG]https://i.gyazo.com/23bc8e3fe7f6f82ecf520251a40ced88.png[/IMG]
[IMG]https://i.gyazo.com/7dafa3d1c6b6d09f12f29b301dc250e2.png[/IMG]
This is the Dedicated Server I got:
[IMG]https://i.gyazo.com/bb0130f05d48812417ffb02915b9c459.png[/IMG]

---

### Post by matt_symes on 2015-11-09
Hi

You have two Ethernet network cards, made by Intel, but no drivers have been loaded for them; hence the UNCLAIMED status.

I'll move you to another sub forum where you're more likely to get some help.

Moved to **Networking and Wireless**.

Kind regards

---

### Post by matt_symes on 2015-11-09
Hi

Please read this.

[http://blog.cuongnv.com/2015/05/xeon-processor-d-1540-10gbe-driver-in.html](http://blog.cuongnv.com/2015/05/xeon-processor-d-1540-10gbe-driver-in.html)

The ports are 10Gb Ethernet ? Are these your NICs [8086:15ad] ?

Kind regards

---

