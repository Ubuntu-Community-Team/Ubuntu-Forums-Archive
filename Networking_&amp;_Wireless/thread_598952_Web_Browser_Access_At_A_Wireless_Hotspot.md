---
title: "Web Browser Access At A Wireless Hotspot"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by usmcgyg on 2007-10-31
Im having a weird problem trying to access the web via a wireless hotspot at an airport. I see the network, am able to connect, but when I open a browser, I get the page not found error. I cleared all cookies, made sure I have no proxy set and still no luck.

I attempted the same thing via windows (still via firefox) and am able to connect successfully.

Any help is greatly appreciated. Although I have not seen this problem before, Im afraid I will see it again and would loike to know the solution.

Thanks

---

### Post by jellymaster2 on 2007-10-31
I was having the same problem with my home network just a couple minutes ago then I turned on the WEP security on my network and it works perfect it looks like ubuntu doesn't like unprotected networks too much :(

---

### Post by JoJerome on 2007-11-01
That seemed to be the issue with my laptop when I installed Gusty. It saw my IBM 2200bg alright and scanned the network ok. But it needed configuring in /etc/network/interfaces...

```

~$ kdesu kate /etc/network/interfaces

auto eth1
iface eth1 inet dhcp
pre-up ifconfig eth1 up


```

Mind you, no idea if that's what's going on with yours and I'm a total newbie myself. But just one of many places to start looking for issues. I imagine someone in the know 'round here will start by asking to see a few such outputs.

- Jo

---

