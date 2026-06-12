---
title: "I can't connect to the wireless network via Ubuntu"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by FastMady123 on 2008-01-06
I can't connect. In the LiveCD, I don't see my wireless network name. This is not easy, unlike Windows XP. 
How to connect to the wireless network via Ubuntu? I know the key, but don't know how to connect and can see the key.

---

### Post by stalker145 on 2008-01-07
> **FastMady123 said:**
> I can't connect. In the LiveCD, I don't see my wireless network name. This is not easy, unlike Windows XP. 
How to connect to the wireless network via Ubuntu? I know the key, but don't know how to connect and can see the key.

To start off with, what kind of hardware are we dealing with? Type```
lshw
```and copy and paste the info here. If you have multiple network interfaces (such as a wired *and* a wireless) then which are you trying to use? 

You can also, if you know all of your hardware, check the [Hardware Compatibility Page]("https://wiki.ubuntu.com/HardwareSupport") to see if it's a problem with your gear not being supported or if others have found workarounds.

---

### Post by FastMady123 on 2008-01-07
The box of the modem/router says it works on Linux

---

### Post by stalker145 on 2008-01-08
> **FastMady123 said:**
> The box of the modem/router says it works on Linux

But does your wireless card work in Linux? That was the purpose of requesting you post ```
lshw
``` here so that we could begin assisting you in troubleshooting. 

More likely than not, a router doesn't care what OS you are using since they all communicate using TCP/IP and do not require drivers.

---

