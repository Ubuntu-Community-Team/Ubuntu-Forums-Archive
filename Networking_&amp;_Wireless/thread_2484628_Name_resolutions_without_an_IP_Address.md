---
title: "Name resolutions without an IP Address"
date: 2023-03-04
forum: Networking &amp; Wireless
---

### Post by securitydad on 2023-03-04
I am running Ubuntu 22.04 LTS, I want to run the system without an IP Address.

However, when I attempt to connect to the Localhost ports, I am blocked, and the error says that they are not ready.

Any suggestions?

---

### Post by him610 on 2023-03-04
>  I want to run the system without an IP Address.
Disconnect from the internet, ie: disconnect the cat 5 cable, turn off your wifi transceiver.
> connect to the Localhost port
From the terminal command line run this...
```
 ping -c2 127.0.0.1 
```
Sometimes one can not avoid using an IP address.

---

