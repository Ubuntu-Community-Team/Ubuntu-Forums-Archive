---
title: "creating wireless network in ubuntu"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by rajeev1982 on 2007-05-24
Hi All,

I have two Dell 640m laptops with Intel Pro 3495 wireless card on it. If I run one of them on Vista and create a wireless network (in vista), the another machine, running on ubuntu, is able to find the ssid and able to connect to that (that means the wireless card is working fine on ubuntu). If I run both the machine on ubuntu and create a wireless conection on one of them, the second machine is not able to seach the ssid of the wireless network which I have configured on the another ubuntu box. I want to connect two ubuntu machine using wireless. Can anybody help me in this.

Thanks in advance.
Rajeev Sharma

---

### Post by ruy_lopez on 2007-05-24
Have you tried changing the mode of the interface. If you look at "man iwconfig" and scroll down to "mode", you'll see this:

```
**mode** Set the operating mode of the device, which depends on the network topology.
The mode can be Ad-Hoc (network composed of only one cell and without Access Point) . . .
```

These modes aren't supported by all cards, so unfortunately just because you card connected to the Vista box, doesn't mean it can initiate a peer-to-peer connection. You should try some of the modes listed in "man iwconfig" and see what kind of results you get, and what the error messages are, if any.

start with this:
```

$ sudo iwconfig (yourinterface) mode Ad-Hoc
```

---

