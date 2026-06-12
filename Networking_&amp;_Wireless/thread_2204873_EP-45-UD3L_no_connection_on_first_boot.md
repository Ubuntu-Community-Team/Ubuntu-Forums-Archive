---
title: "EP-45-UD3L no connection on first boot"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by fred23 on 2014-02-10
Seems I can't get a connection (Local or internet) after boot, I got disconnection errors all the time. Eth0 is recognized with DHCP configured as default. Same PC booting with windows or OSx have perfect working LAN on DHCP. 

Green LAN disabled in Bios.

---

### Post by varunendra on 2014-02-13
Welcome to the forums fred23!

> **fred23 said:**
> Green LAN disabled in Bios.

What do you mean by above?

Please open a terminal (Ctrl-Alt-T) and show us the outputs of -
```
sudo lshw -numeric -C network -sanitize
ifconfig
nm-tool
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

