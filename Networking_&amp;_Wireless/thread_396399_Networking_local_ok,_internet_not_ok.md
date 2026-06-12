---
title: "Networking: local ok, internet not ok"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Robert Leithe on 2007-03-29
Hi,

I switched my PC off this afternoon. Came back this evening and switched it back on. After logging on I find I cannot connect to the internet.

I'm receiving a DHCP address from my router, and can ping and access computers internally. However, I cannot access the "outside world". I'm runnnig Ubuntu 6.10 on Dell Inspiron 9300 and are using the internal network interface. It's been working flawlessly up till now.

Any ideas as to how/what I should look for to get back online?
(Please bear in mind that I'm still a bit of a Linux newbie... :)

Sincerely

EDIT: I should mention that other computers connected to the same router (such as the one I'm writing on right now) have no problems connecting to the internet.

EDIT2: When I quit Firestarter there are no problems connecting to the internet. Somehow the configuration of Firestarter prohibits the connection.

---

### Post by JengaBlocks on 2007-03-29
Check to see if you added a route to the gateway:
  route add default gw ipaddress eth0

---

### Post by Robert Leithe on 2007-03-29
I will repeat my EDIT2 from the original post in case not everyone notices:

"When I quit Firestarter there are no problems connecting to the internet. Somehow the configuration of Firestarter prohibits the connection."

---

