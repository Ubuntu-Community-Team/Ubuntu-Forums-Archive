---
title: "Configuring a new ethernet card"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by Hex_Mandos on 2007-01-01
A few weeks ago, a storm fried my onboard ethernet port. Since then, I've been using my cable modem through USB, without any need for configuration (I was surprised at this).

However, as I'm going to switch ISPs, I want to have a connection through an ethernet card. I installed my card (NIC PCI 3Com Etherlink XL) a few days ago, and Ubuntu won't recognize it. I disabled the onboard port in the bios setup to avoid any detection problem, but I still can't connect using my ethernet connection.

Running ip link from terminal I get this result

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:04:75:71:d8:b1 brd ff:ff:ff:ff:ff:ff
4: sit0: <NOARP> mtu 1480 qdisc noop 
    link/sit 0.0.0.0 brd 0.0.0.0
5: eth2: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:14:04:aa:22:61 brd ff:ff:ff:ff:ff:ff

Does someone know how to install my card? Also, what are eth1 and eth2? (my onboard port is eth0 when I enable it).

---

### Post by chippy99 on 2007-01-01
Try runing the following command
sudo insmod 3c515
This should load the driver for your nic.
If it works you will need to add this module to /etc/conf.modules so that it loads at bootup.

---

### Post by Hex_Mandos on 2007-01-02
Thanks, but apparentyl Ubuntu IS recognizing the card after all. It's eth2:
[http://www.ubuntuforums.org/showthread.php?t=329354](http://www.ubuntuforums.org/showthread.php?t=329354)

Now I just need to configure it so that it works with my modem.
(Also, I'd stop using this thread. I don't want to spam the forums with my problem. I just didn't want to leave chippy99 without a reply).

---

