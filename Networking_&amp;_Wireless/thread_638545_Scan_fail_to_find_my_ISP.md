---
title: "Scan fail to find my ISP"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by orengt on 2007-12-12
when running pppoeconf I got a message that my ISP cannot be found and that I need to check my HW but it should be ok since it works with Windows XP. 

My network board is: Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC  and my Cable modem is Motorola SB 4200. 

The following is from the system.log:
[   73.373701] r8169: eth0: link up 
[   83.771874] eth0: no IPv6 routers present 
[   88.202027] r8169: eth0: link up 
[   90.319819] r8169: eth0: link up 
[  110.812849] eth0: no IPv6 routers present 
[  279.076120] PPP generic driver version 2.4.2 
[  279.079870] NET: Registered protocol family 24 

Can someone tell what is wrong?

OrenG

---

### Post by d0nny2600 on 2007-12-12
Can you ping out?

---

### Post by orengt on 2007-12-12
No I can't ping, I tried both my ISP DNS server and ubuntu.con.

---

### Post by d0nny2600 on 2007-12-13
Have you been assigned an IP or are you set at localhost ?

---

### Post by orengt on 2007-12-13
How can I check if an IP was assigned?

---

