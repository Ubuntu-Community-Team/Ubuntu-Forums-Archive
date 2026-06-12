---
title: "problem accessing my site on 9.10 server"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by sourabhtrc on 2010-03-10
Hi,
 
I have recntly switched to ubuntu 9.10 desktop edition and installed the LAMP package. It seems that I can access my website (using IP address) which is in the /var/www/ folder locally but not from outside the range of my router. any system which is not running on my router can not connect to my site.

Can anyone please tell me what the problem might be and what can be the solution to this?

---

### Post by louieb on 2010-03-10
Set your router up to forward port 80 to the server.

If you don't have a static IP from your ISP - you willl need to use a service like dyndns.com.

---

### Post by holeyness on 2010-03-10
Check your firewall of your router and then have your router forward port 80 to "your computer's ip address on the local network" e.g. 192.168.X.X or 169.254.X.X

---

