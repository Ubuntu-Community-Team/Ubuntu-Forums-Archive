---
title: "Help Needed Setting Up Internet Connection"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by 330033 on 2011-03-20
My Internet Service Provider(read=guy;)) has changed his connection from a wireless-only setup to one requiring both a wireless connection and a simultaneous WAN Miniport(PPPOE) connection. I have a dual-boot PC, so configuring said setup on the Windows side was relatively easy; replicating this on the Linux side has not been so. I have to admit that i am a bit of a noob however, so my difficulties are to be expected and this is now an opportune time to learn something new. Can anyone please help me?

---

### Post by dineshs on 2011-03-20
Hope your wireless card is working fine on ubuntu and  you are using network manager for configuring network connections .Assuming your wireless interface is wlan0 (You may check using *ifconfig -a*) ,Run ```
sudo pppoeconf wlan0
```and follow instructions to create the connection.
Now run ```
sudo pon dsl-provider
``` to connect and ```
sudo poff dsl-provider
``` to disconnect.

---

### Post by 330033 on 2011-03-20
> **dineshs said:**
> Hope your wireless card is working fine on ubuntu and  you are using network manager for configuring network connections .Assuming your wireless interface is wlan0 (You may check using *ifconfig -a*) ,Run ```
sudo pppoeconf wlan0
```and follow instructions to create the connection.
Now run ```
sudo pon dsl-provider
``` to connect and ```
sudo poff dsl-provider
``` to disconnect.

Worked Perfectly. :-) Thank you :-).

---

