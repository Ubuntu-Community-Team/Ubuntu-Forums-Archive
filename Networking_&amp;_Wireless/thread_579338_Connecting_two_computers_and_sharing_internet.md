---
title: "Connecting two computers and sharing internet"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by Repabil on 2007-10-18
Hello,

I'm trying to connect my desktop to my laptop to share files and internet. I've tested so that all network cards work with their drivers. My setup:

Desktop:
eth1: connection to broadband internet and working
eth0: connected to laptop via crossover cable

Laptop:
eth0: connected to laptop via crossover cable

I want the Desktop to act as a firewall to the laptop so I set firestarter in it to connect eth0 to the lan and eth1 to the internet. I've tried setting a static ip to to eth0 in desktop and eth0 in the laptop one tpo and refering eth0 in desktop as gateway to the laptop. But when I try to ping between them it's unsuccesfull. I've also tried not setting static ip on the laptop and enabling a dhcp server via firestarter but it fails to start the server. Also when run firestarter in the terminal I get an error merror message as its run:```
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `DROP'
```

Would appreciate any help.

---

### Post by tkharris on 2007-10-18
Why don't you buy a router?  Or a switch if you have more than one IP address?

If you want just a firewall out of the desktop I would recommend using pf on OpenBSD over Ubuntu.

---

### Post by louie55 on 2007-10-18
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by Repabil on 2007-10-19
> **tkharris said:**
> Why don't you buy a router?  Or a switch if you have more than one IP address?

If you want just a firewall out of the desktop I would recommend using pf on OpenBSD over Ubuntu.
I'm gonna use the desktop to play music and file server aswell so I need a gui on it. Also it seems I only get one IP address from my ISP.

---

### Post by bigken on 2007-10-19
you have to manually set the ip addresses 192.168.0.1 and 192.168.0.2

subnet mask 255.255.255.0
default gate way 192.168.0.1

---

### Post by Repabil on 2007-10-19
> **bigken said:**
> you have to manually set the ip addresses 192.168.0.1 and 192.168.0.2
I did set the ip on the desktop to 192.168.0.1 and the ip on the laptop to 192.168.0.2 aswell as its gateway to 192.168.0.1.

---

### Post by bigken on 2007-10-19
what is your default gateway ?

what is the ip address your provider gives you ?

---

### Post by bigken on 2007-10-19
what im saying is if your gateway is 192.168.2.1 then your ip addresses would be 192.168.2.1 and 192.168.2.2

---

