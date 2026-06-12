---
title: "Ubuntu 20.04 unable to install my LAN driver properly"
date: 2023-08-26
forum: Networking &amp; Wireless
---

### Post by ahmedo2452 on 2023-08-26
My Ubuntu 20.04 isn't able to install the networking driver properly (which is Realtek PCIe FE Family Controller), It recognizes the connection, but NOT the internet (I'm writing this from a Windows 8.1 PC)

Why this happened? And how to fix this error?

---

### Post by chili555 on 2023-08-26
> It recognizes the connection, but NOT the internetPlease run and post:

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

There is no need to post the entire result; just tell us the packet loss for each. Also run and post:

```
ls -al /etc/resolv.conf
```

---

### Post by ahmedo2452 on 2023-08-28
I have runned:
ping [www.google.com](www.google.com)
And it says NO internet.

---

### Post by chili555 on 2023-08-28
> **ahmedo2452 said:**
> I have runned:
ping [www.google.com](www.google.com)
And it says NO internet.What about the other data I requested? We need that information in order to propose a solution.

---

