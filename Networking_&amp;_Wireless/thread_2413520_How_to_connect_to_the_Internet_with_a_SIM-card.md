---
title: "How to connect to the Internet with a SIM-card?"
date: 2019-02-26
forum: Networking &amp; Wireless
---

### Post by udippel on 2019-02-26
I have read many posts in here and elsewhere with lots of details that I don't understand.
I have not been able to find any that explains clearly what to do in order to connect. 

Almost everyone talks about some modem-manager. When I run it, it says 
$ network-manager
network-manager: command not found
When I want to install it, it says
$ sudo apt-get install network-manager
[...]
network-manager is already the newest version (1.10.6-2ubuntu1.1).

Is there no GUI to do that? If not, I can always use the text interface. But I need to know what I have to write. I know there is a working device that connetcs, since it is a dual-boot with W10, and it works in W10. 

What to do?

---

### Post by praseodym on 2019-02-26
Start it from terminal with

nm-connection-editor

---

### Post by stevencarle93 on 2019-04-12
I have the same problem and I tried to do it from the Network Connections editor, creating a new Mobile Broadband connection but It didn't work. Do you know what kind of information I need to know to create the connection correctly? Thank you very much and I will be waiting for your response.


This is the Thread that I created to report my issue. If you can answer there I will be grateful: [https://ubuntuforums.org/showthread.php?t=2416643&p=13851344#post13851344](https://ubuntuforums.org/showthread.php?t=2416643&p=13851344#post13851344)

---

