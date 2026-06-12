---
title: "Connecting to WiFi and Hardwire"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by ben115 on 2014-11-04
I have an Ubuntu 12.04lts laptop connected to an intranet via a hardwired ethernet connection with no internet access.  The laptop also connects to a local wifi router which has internet connectivity.  

So, how on the laptop would I browse the internet?

---

### Post by pfeiffep on 2014-11-04
Possibly set up a proxy in your browser

---

### Post by Bucky Ball on 2014-11-05
Probably a question for whoever is running the intranet/router. Please give more detail about the setup. Is this in a business or institution or at home? Do you have all details of both the router and the intranet?

---

### Post by ben115 on 2014-11-13
This isn't a business or institution intranet.  I figured out how to solve it.  Don't remember what forum I found this on, but the gateway for both the intranet and the router had to be the same.  So, I did:
```
sudo route del default gw 111.111.1.1
sudo route add default gw 222.222.2.2
```

Where 111.111.1.1 was the gateway for my intranet connection, and 222.222.2.2 was the gateway for the router I wanted to connect to the internet on.

---

