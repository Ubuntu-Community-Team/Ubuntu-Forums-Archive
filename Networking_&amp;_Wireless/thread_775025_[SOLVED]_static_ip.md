---
title: "[SOLVED] static ip"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by terry f on 2008-04-29
Hi

I am having a hard time setting up a static ip address on my desktop, I am using a wireless connection.  After I make it static I can't connect to my network. Can any one tell me what to do so I can get this work.

---

### Post by superprash2003 on 2008-04-29
have you entered the details such as gateway,subnet etc when setting up static ip?

---

### Post by terry f on 2008-05-01
yes i have.

---

### Post by superprash2003 on 2008-05-01
are you able to ping your gateway(router) once you setup static ip?

---

### Post by terry f on 2008-05-01
no, I cant connect to my router so I cant ping anything besides my self.

---

### Post by mbdriver on 2008-05-01
the dns is the problem. can`t config manualy. waiting for someone that have the solution for this problem.

---

### Post by helgman on 2008-05-02
Can you connect to the wireless when your using a dynamic address?

Can you associate with the AP when using static?

Are you using any kind of encryption?

Regards,
Helgman

---

### Post by terry f on 2008-05-02
Can you connect to the wireless when your using a dynamic address?: yes

Can you associate with the AP when using static?: no

Are you using any kind of encryption?: yes wep

---

### Post by helgman on 2008-05-03
[Here](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html) is some information about troubleshooting wireless. They assume you want to use DHCP but just skip that part (dhclient) and go for a static assigning of address (ifconfig).

I've never worked with WEP but it looks pretty straight forward.

Does it help you at all (that is, can you associate etc)?

Regards,
Helgman

---

### Post by terry f on 2008-05-03
Thanks got it working now.

---

