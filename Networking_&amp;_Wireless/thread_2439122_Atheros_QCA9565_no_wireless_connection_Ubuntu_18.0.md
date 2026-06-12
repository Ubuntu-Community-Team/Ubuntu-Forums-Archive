---
title: "Atheros QCA9565 no wireless connection Ubuntu 18.04"
date: 2020-03-23
forum: Networking &amp; Wireless
---

### Post by bigcola3 on 2020-03-23
Hi,

I have Ubuntu 18.04 installed on my system and while I have been able to use my wireless home connection in the past on the same system, recently it does not connect to the internet.
In particular, it appears to connect to the network in NetworkManager, but the icon displays a question mark, and internet is in fact not available.

What I believe is bizarre, is that I can access internet by connecting via wired Ethernet, and when I do so the question mark on the wireless connection icon also disappears.

I have attached the log from the wireless-script [ATTACH]285260[/ATTACH].

I hope you can help,
Luca

---

### Post by vincentur802 on 2020-03-23
Has there been any environmental or infrastructure changes to your network? i.e. new NIC, new router, different network configurations.

It may help to restart the network manager: 
sudo systemctl restart network-manager

[FONT=arial]Also make sure your wireless interfaces aren't blocked:
[/FONT]
sudo rfkill unblock all

---

### Post by bigcola3 on 2020-03-23
Thanks for your reply.

No change that I'm aware of, but the network works fine with all my other devices.

I just tried both things you suggested, but I also tried several others today and none seemed to fix the issue. 
The only thing I fear is that I may have messed up some configuration file a while ago, while configuring port forwarding for a board I'm working with, but I don't know if that is the case.
Yet I do not know how to debug the issue further.

Restarting Network Manager removes the question mark from the icon in the desktop panel, though it's still there in the drop-down menu.

---

