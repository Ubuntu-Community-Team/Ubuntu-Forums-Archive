---
title: "Ethernet Bridge Question"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by plwilming on 2010-02-02
I've just finished installing ubuntu server on my desktop and I wast to know if I hook up an ether net bridge from my router to my desktop will it still work. I'm just using it as a web server and I'm not sure if I could even use a wireless adapter. I just don't want to leave it in my living room next to the router anymore, and god forbid I move the router from the two Xboxes. =P


Thanks for any help. =D

---

### Post by desperado665 on 2010-02-02
A bridge really consists of only 2 routers connected to each other and is used to connect two network segments of different protocols (TCP/IP to MacTalk, for example). I don't see why you would need to bridge at all, much less between your router and desktop.

---

### Post by ubunterooster on 2010-02-03
I see no reason this would not work. 
Experiment!

---

### Post by theozzlives on 2010-02-03
If you want to your desktop/tower as a web server just install Apache and in your router forward port 80 to the IP of the server. You'll need to configure your router to act as a DHCP server so your server has it's own static IP. You'll also need a static IP with your ISP and register your fully qualified domain name with a registrar. I did the same with my site (link is below).

---

