---
title: "firewall rule for file sharing"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by manny43 on 2010-02-18
Hello friends

In order to share a file in home network(Ubuntu-Windows) i  have to disable firewall all the time.Is there a way to allow network to see Ubuntu pc and firewall still deny incoming traffic?What rule must be applied?
Thanks for your help.

---

### Post by HarrisonNapper on 2010-02-18
Should just be able to create a rule to allow incoming traffic from the internal IP of the windows comp. Can be done with iptables or a frontend like Firestarter.

---

### Post by manny43 on 2010-02-18
Thank you for your help.I'm trying to create a rule but gufw in advanced option is asking for a "from" IP address and "to"
IP address.My quiestion is should both IP adress be the same and also which port number is the right one?1 or 2.

---

### Post by marquinos on 2010-02-19
Hi!
Yes. Set by defect Gufw = Deny all rules (Green shield).
Add a rule (advanced tab) for your IP & Port of Windows as FROM (You will share Ubuntu files FROM other computer ;)

As example: your other computer is IP 192.168.1.1 and you will use the port 98.
Add this rule in advanced tab:
Allow TCP From 192.168.1.1   98 (The "to" row empty).

Best regards!

---

### Post by manny43 on 2010-02-19
Thank you very much..............................SOLVEEEEDDDDDDDDDDDDDDDDD THANKS

---

