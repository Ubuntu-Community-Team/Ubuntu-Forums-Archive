---
title: "How to remote login via XDMCP from xubuntu?"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by r00dy on 2007-05-25
Hi everyone
I'm fresh xubuntu user. I hope I'm posting to the right forum. 
I cannot find how to login to remote X via XDMCP. 
I've checked in user GUI and in config files and on login screen I'm able only to choose xfce, last session or failsafe. What should I enable to choose remote login on login screen?

Thanks in advance

---

### Post by b1g4L on 2007-05-28
I am also trying to figure this out. I have Ubuntu Feisty on my Desktop and XUbuntu on my laptop. I'm trying to remote into my Desktop from the laptop. There is no option for a "Remote Login via XDMCP" on XUbuntu.

---

### Post by r00dy on 2007-05-29
I have figure it out. 
In Login Window Preferences go to Security and click on "Configure X Server".
Then change server to start from Standard to Chooser.

---

### Post by b1g4L on 2007-05-30
Awesome - I'll try this when I get off work. Thanks for posting back...

---

### Post by r00dy on 2007-05-30
No problem. 
BTW should XDMCP work smooth over WiFI 11Mbps connection? For me it's running quite slow, but maybe I have something with my cards (pings are about 30ms).

---

