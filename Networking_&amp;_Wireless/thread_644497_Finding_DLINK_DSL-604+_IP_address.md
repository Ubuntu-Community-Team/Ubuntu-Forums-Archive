---
title: "Finding DLINK DSL-604+ IP address"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by simpsonsfreak on 2007-12-18
Hi everyone,
I'm connected to internet on my Ubuntu computer through the wireless part of the D-link DSL-604+, but I need to change some settings in the DSL-604+ (Pidgin cannot connect anymore). The problem is, I don't know the IP address of the DSL-604+. Is there any way I can find out its IP address from Ubuntu? (The DSL-604+ is attached to an ADSL modem, which is showing up as the gateway IP).

Thanks,

---

### Post by mellowd on 2007-12-19
> **simpsonsfreak said:**
> Hi everyone,
I'm connected to internet on my Ubuntu computer through the wireless part of the D-link DSL-604+, but I need to change some settings in the DSL-604+ (Pidgin cannot connect anymore). The problem is, I don't know the IP address of the DSL-604+. Is there any way I can find out its IP address from Ubuntu? (The DSL-604+ is attached to an ADSL modem, which is showing up as the gateway IP).

Thanks,

Yup. The router will be your gateway so do it like this:

Open up a terminal and type this

```
sudo aptitude install traceroute
```

Then in the same terminal type this:

```
traceroute www.google.com
```


The first hop should be your gateway, that is if you see a packet going to 192.168.1.1 first and then onwards you know that 192.168.1.1 is your gateway/router.

---

