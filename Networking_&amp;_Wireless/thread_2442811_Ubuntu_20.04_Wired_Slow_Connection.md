---
title: "Ubuntu 20.04 Wired Slow Connection"
date: 2020-05-07
forum: Networking &amp; Wireless
---

### Post by andreilica on 2020-05-07
I have just installed Ubuntu 20.04 and I am facing a pretty big issue. My download speeds are really low compared to the Windows 10 that I have installed on dual-boot setup. Here you can see the difference: [[Pictures]("https://imgur.com/a/yxjvL9K")].

My network adapter is Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller. 

I have tried changing the DNS options but that doesn't help. 
Also I've installed "r8168-dkms_8.048.02-1_all.deb" instead of r8169 which I've added into blacklist.conf. Still the same issues.
Any suggestions? 
Thank you!

Device is a Lenovo Y700-15ISK Laptop.


[[lshw output]]("https://pastebin.ubuntu.com/p/Vv5HgVpRN8/")


Also, the ifconfig shows a lot of dropped RX packages that are increasing as we speak: [[Evidence]("https://imgur.com/a/mcJpN1w")]

---

### Post by gary.allan.garibaldi on 2020-05-07
Not sure if this will hep you but it did fix my problem.

sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service

---

### Post by CelticWarrior on 2020-05-07
> **gary.allan.garibaldi said:**
> Not sure if this will hep you but it did fix my problem.

sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service

No, it won't help at all.
Why do you think something to change the power saving profile of a WiFi would help with Ethernet?

---

### Post by andreilica on 2020-05-08
Yeah, on Wi-Fi the speeds are even slower than that, but that's kinda normal. The router only support 100Mbits/s on Wi-Fi. I still think that it's a driver issue because I can see that RX packets drop increase as we speak. It's the same behavior on r8169 also. Maybe no driver yet compatible witb 20.04?

---

### Post by gary.allan.garibaldi on 2020-05-08
Sorry. Miss read your post.

---

### Post by praseodym on 2020-05-09
Change the mtu-value in your network profile to a number instead of "Automatic". Check your ISPs info for that

---

