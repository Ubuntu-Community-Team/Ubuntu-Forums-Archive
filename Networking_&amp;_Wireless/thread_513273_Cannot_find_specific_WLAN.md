---
title: "Cannot find specific WLAN"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by quattroman on 2007-07-30
Good morning.

I have this problem with my DWL-G650 airplus extreme G.  I can find all wireless networks I want, but I can't my jobs signal.

I even tried using "Connect to other wireless network..." and adding all the information by hand, but still nothing.

What can be causing this?

---

### Post by bash4fun on 2007-08-01
what do you mean by your jobs signal?
you could try connecting by using
"iwconfig" in a terminal and specifying
all relevated options

---

### Post by Shib on 2007-08-01
what does

```
sudo iwlist wifi0 scan
```

(or ath0, eth0... etc) give you?

---

