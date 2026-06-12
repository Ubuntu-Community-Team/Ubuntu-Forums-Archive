---
title: "Configeration problems"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by derrylynne on 2007-01-01
I have a strange problem with my wireless card and router. It only half works. When I first connected the card it as recognised but Firefox had a DNS problem. It would connect if I put in the ip address but not if I put in say [www.google.com](www.google.com). I resolved that one by changing a configuration setting in Firefox but my computer hangs if I go for updates and if I try to pick up email. As he card works well I tend to think it is some configuration problem. Has anyone else had this problem and resolved it? If I connect my Ethernet router to this laptop instead everything works fine – making the problem stranger but I want to be able to use the wireless card as it is more convenient....

---

### Post by mojoman on 2007-01-01
Try pinging google

```
ping -c 3 72.14.203.99
```

This should ping it 3 times. If it does, you have Internet connection and if you can't access [www.google.com](www.google.com) this could indicate a problem with nameservers. To exclude any problems with your browser, you could use links to check out [www.google.com](www.google.com) through the terminal (just ```
sudo apt-get install links
``` and then type ```
links
``` in the terminal to start this neat little non-graphical browser, which is a very good tool to have at hand).

Name servers are stated in /etc/resolv.conf. Going through a router, you should have the router address, unless you have static name servers, in which case you should have those numbers entered (I think).

Best regards
/Mojoman

---

