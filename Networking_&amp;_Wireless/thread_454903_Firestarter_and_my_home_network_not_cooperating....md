---
title: "Firestarter and my home network not cooperating..."
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by mistaWAC on 2007-05-26
In a nutshell:
>>Trying to connect my Ubuntu box to my other WinXP boxes via Samba and it doesn't work when the firewall is up (Firestarter; Ubuntu Box).

Details:
>>In my home there are four other computers in my workgroup (three wired desktop and a wireless laptop).  There is a fifth computer, the Ubuntu server, that is also on the network.  The problem I'm having is that I have Firestarter installed on Ubuntu and would prefer to always have it running considering I'm running an FTP server out of it and it's always on.  When the firewall is up in Firestarter, I cannot access the server from my other computers.  I've tried setting a few different policies, but none work.  When the firewall is down, I can access the server.

How do I configure this whole setup to work WITH Firestarter on?

---

### Post by coffeecat on 2007-05-26
You don't give details of how you tried to add policies, but I had similar problems when I tried to allow connections from particular hosts under Policy > inbound traffic. If that's what you did, try right-clicking on the lower pane (Allow service) instead, choose 'add rule' and then choose whatever services you want for 'Allow Service'. Don't forget to click the 'Apply Policy' button. Easily missed.

---

### Post by mistaWAC on 2007-05-26
got it...thanks

---

