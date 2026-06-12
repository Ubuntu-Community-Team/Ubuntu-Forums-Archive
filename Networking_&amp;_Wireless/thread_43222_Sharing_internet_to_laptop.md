---
title: "Sharing internet to laptop"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by SadnesS on 2005-06-21
Hello.

I have "main" computer which is connected to ADSL. I need to share internet connection to my laptop machine. Computer (this) has two network cards, Realtek 8139 and motherboard inter. SiS network card. 

Here is some info this computer which is sharing internet:
Ubuntu Hoary (latest updates)

here is my laptop:
Compaq Armada 110 
Ubuntu Hoary (latest updates)

Here is some info network system:

SiS (eth0):
DHCP is on

Realtek 8139 (eth1) (crossover on laptop):
No DHCP
Ip: 192.168.0.1
Submask: 255.255.255.0

Here is my laptop:
No DHCP
Ip: 192.168.0.3
Submask: 255.255.255.0
Gateway: 192.168.0.1

I have used Firestarter to share internet but if it works, it is so damn slow (feels like use modem) or Firestarter crash. I have make things with this tutorial: [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

What i can do to make all things work? 

Sorry my bad english.  ](*,)

---

### Post by defkewl on 2005-06-21
Have you tried iptables?

---

### Post by SadnesS on 2005-06-21
[QUOTE=defkewl]Have you tried iptables?[/QUOTE]

Well, i tried something called MASQ..... Didin't work. 

I have been readed iptables manuals, but i have no clue, what i have to do.

---

