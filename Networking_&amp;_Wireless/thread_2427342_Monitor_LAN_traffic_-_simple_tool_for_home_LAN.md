---
title: "Monitor LAN traffic - simple tool for home LAN"
date: 2019-09-20
forum: Networking &amp; Wireless
---

### Post by holiday on 2019-09-20
I am having some dips in bandwith that cannot be explained by any activity I know about. 

I have looked at Nagios but it is more than I need. I don't need an elaborate UI and I don't want to have to install and configure apache. 

Hoping for a simple commandline tool.

Anything?

---

### Post by fragglebliss on 2019-09-21
That's easy. bmon, nload, tcpdump

---

### Post by holiday on 2019-09-21
As far as I can tell these all monitor traffic on the machine that is running the application. I want to monitor traffic that is running through the *LAN* i.e. monitor traffic to all the devices connected to my router. My router doesn't offer much in the way of logging.

At any time, I have a number of devices connected to my LAN and I want to know which device is the hog.

---

### Post by him610 on 2019-09-21
holiday, here is crude, simple, effective method that only requires one additional network adapter for your PC (assuming wired LAN)
```

    ISP
     |
     |
Cable Modem
     |
     |  <--Cat5e cable
     |
  Your_PC
     |
     |
  Router
  |  |  |
  |  |  |
 Other_PCs
  on LAN

``` 

Others may suggest a more elegant solution

---

### Post by fragglebliss on 2019-09-22
> **holiday said:**
> As far as I can tell these all monitor traffic on the machine that is running the application. I want to monitor traffic that is running through the *LAN* i.e. monitor traffic to all the devices connected to my router.Yes, my suggestions do exactly that. But you never mentioned otherwise in your original post. Perhaps you should implement a software based router into your network that would handle proper logging for all connections. That would be my suggestion as hardware modems/routers are terrible for logging traffic and troubleshooting.

---

### Post by holiday on 2019-09-22
Ah I see. Thank you both. A project that is a bit more interesting than I thought.

---

