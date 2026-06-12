---
title: "No wlan0, wlan2 instead + wireless autoconnect w/ wpa"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by coverslide on 2009-11-06
[LEFT]So I messed with my /etc/network/interfaces trying to get my wireless device to connect to my router, and something went wrong, and it wouldn't start up, so I had to hard reset a few times till I could change it back to just:

```

auto lo
iface lo inet loopback
```

When I was able to get back in, I found out that my wireless device was no longer called wlan0, but wlan2 instead. So, my first question is this:

1) How do I change the name of my device back to wlan0?

and also,

2) What is the right way to connect to a wireless device with a wpa psk? Both manually and automatically on startup?
[/LEFT]

---

### Post by diesch on 2009-11-06
> **coverslide said:**
> [LEFT]When I was able to get back in, I found out that my wireless device was no longer called wlan0, but wlan2 instead. So, my first question is this:

1) How do I change the name of my device back to wlan0?


In /etc/udev/rules.d/70-persistent-net.rules remove the entries you don't need (or remove the file if you don't need an entry there - a new one will be created at the next boot).
[/LEFT]

---

