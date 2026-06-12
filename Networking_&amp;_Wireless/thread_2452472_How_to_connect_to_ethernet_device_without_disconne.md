---
title: "How to connect to ethernet device without disconnecting wifi?"
date: 2020-10-22
forum: Networking &amp; Wireless
---

### Post by mysteriousmonkey29 on 2020-10-22
Hello, I am running ubuntu 18.04, kernel 5.4.0-42-generic. I am trying to communicate with a hardware device over an ethernet connection. I am able to do this by setting a manual static IP address in the settings/network section. I am also able to connect to wifi. However, I am unable to do both simultaneously. As soon as I plug in the ethernet cable, the wifi switch in the settings menu goes off, and I can't turn it back on until I unplug the cable. I tried disabling the "connect automatically" on the ethernet network settings, and also checking the "use this connection only for resources on its network" checkbox under the Routes section. But no dice.

I have found a lot of similar forum posts, but either they're not running the same version of ubuntu as me, or they don't have the same settings menu. They reference a "disconnect on wired connection" checkbox under the wifi settings, which I do not see on my end. They also frequently reference changing settings in "network manager", but I don't have such an application. I am accessing settings by clicking the start menu, and then typing in settings.

Any ideas? Help would be greatly appreciated!

---

### Post by eby on 2020-10-26
If this happens on a Laptop, check bios/firmware settings, some laptops have disable lan on wifi connection or vice-versa.

---

### Post by kc1di on 2020-10-26
As has been said it's usually a bios setting not a software setting.  So check you bios.

---

### Post by SeijiSensei on 2020-10-26
The two interfaces should be on separate subnets, e.g., 192.168.1.0/24 for the wifi, and 192.168.2.0/24 for the wired connection. Otherwise you can encounter routing problems. 

If you need to communicate between the subnets, make sure to uncomment the line
```
net.ipv4.ip_forward=1
```
in /etc/sysctl.conf and then run "sudo sysctl -p" to reload the configuration.

---

### Post by mysteriousmonkey29 on 2020-10-26
Ok, cool, I found the bios settings and disabled them--unchecked both "control WLAN radio" and "Control WWAN radio" under power management-->wireless radio control. Now I can have both connected at the same! Or at least nominally.

As SeijiSensei suggested, I also changed the subnet of my hardware device and connection to be a different subnet than that of the wifi. However, it seems the connections are still interfering with each other. When the hardware device is on and plugged in, my wifi connection goes out (although it still claims to be connected in the settings).

Any ideas?

Thanks everyone!

---

### Post by mysteriousmonkey29 on 2020-10-26
Actually, stratch that. They just started working in parallel now! Not sure what the problem was, or how it worked itself out. I will repost again here if it stops working again.

---

