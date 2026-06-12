---
title: "network hangs, unexplainable. It does it randomly along with desktop hanging/freezing"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-03-18
Why is this? wtf is happening in xubuntu? Any reaosn why my network will randomly hang and timeout in xubuntu? I need a fix for this ASAP as i'm unsure when the next time i'll be able to get on the ubuntu forums as it randomly lags for me.

---

### Post by OffAxis on 2009-03-18
if it started happening out of nowhere it could be a hardware issue; a dying router, NIC, or bad connection. A lot of times these issues are intermittent, which makes them frustrating to track down.

The next time it happens, try pinging your loopback address

```
ping -c 4 localhost
```

if that's okay then try your router

```
ping -c 4 192.168.1.1
```

(assuming that's your router's ip)

if that works try a website
```

ping -c 4 google.com
```

if that all works it may be your browser, so try a different browser.

---

### Post by 133794m3r on 2009-03-18
ok, i'm currently getting a second browser and i'll try those steps next time it happens i'll make a txt document with it. I'm just hoping this old laptop which is my backup since my current's in repair'll last till i get my new one back.

---

### Post by 133794m3r on 2009-03-18
yeah i did what you said hwen it happens local host works router unsure since i'm on the school net so i just tried to ping google.com it came up as unknown host. :/ the only way i've found to fix it is to reboot. so yeah lovely life this is.

---

### Post by 133794m3r on 2009-03-21
bump

also how can i reinstall the driver? i just would like this to fix it since the driver might be going bad(i can hope atleast).

---

