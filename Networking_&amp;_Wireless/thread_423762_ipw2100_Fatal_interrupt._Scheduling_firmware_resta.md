---
title: "ipw2100: Fatal interrupt. Scheduling firmware restart."
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by _lux on 2007-04-26
Hi,

i get a strange effect.

I worked normally with my notebook via WLAN (Centrino ipw2100 with WPA2, configured via network manager).

I shut the notebook down and started it two hours later.

When I look at the wlan networks (iwlist eth1 scanning), I can see our net but I can not connect. Syslog gives the error message "Fatal interrupt. Scheduling firmware restart.".

Any idea?

Thanks for your support!

Dirk

---

### Post by saltydog on 2007-11-08
I have exactly the same behaviour on my ThinkPad X31 qith ipw2100. Could it be a bug of the card's driver?

---

### Post by omgitsmit on 2008-06-17
> **saltydog said:**
> I have exactly the same behaviour on my ThinkPad X31 qith ipw2100. Could it be a bug of the card's driver?

I am having the same issues as well. A quick google search revealed other distros (Fedora, OpenSUSE) have also been experiencing this issue and have filed bug reports.

Anything else we can try?

---

### Post by Vasto on 2008-06-19
Would your router happen to be a 2Wire?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793)

---

### Post by omgitsmit on 2008-06-22
> **Vasto said:**
> Would your router happen to be a 2Wire?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793)

No. This is happening from an Embedded wireless card in a Laptop to a Linksys Wireless Router. I'm still having complete drop outs and the following message in my logs:


```
ipw2100: Fatal interrupt. Scheduling firmware restart.

```

Help!

---

