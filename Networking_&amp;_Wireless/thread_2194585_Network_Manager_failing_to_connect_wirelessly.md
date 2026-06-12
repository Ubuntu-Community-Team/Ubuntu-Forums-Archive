---
title: "Network Manager failing to connect wirelessly"
date: 2013-12-19
forum: Networking &amp; Wireless
---

### Post by goodbye300 on 2013-12-19
I am running LUbuntu (Ubuntu + LXDE) on an IBM Thinkpad T41.

I'm having trouble connecting to a wireless network it can see, but I am not receiving any error message to tell me why not.

It's not an encryption issue. The network is open, and has good signal strength. It is seen by NetworkManager.

I've tried killing NetworkManager and running

```
NetworkManager --no-daemon --log-level=DEBUG
```

But I cannot do that because something else will immediately spawn another NetworkManager running. 

```
sudo service NetworkManager stop
```

does not work because there is not a service for NetworkManager.

---

### Post by tfrue on 2013-12-20
Goodbye300,

Hate to hear about your wireless issues, so if you would be so kind please post the output from these commands:
```
lspci
```
or if you are using a usb wireless interface:
```
lsusb
```

And one more:
```
ifconfig -a
```
Thanks,
Chris

---

