---
title: "Change default html port on Ubuntu Server"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Arwen17evenstar on 2011-05-17
I followed the directions [here]("http://www.cyberciti.biz/faq/linux-apache2-change-default-port-ipbinding/") to change the listening port 80 to port 8000.

If I type 192.168.1.123:8000 into a web browser, it doesn't work.

I can access my webpage just fine at 192.168.1.123 when I have the ports.conf file set to Listen on port 80

but I can't get this to work with port 8000. why?

I have my router properly forwarding 8000 to 192.168.1.123, but I'm trying to access inside my LAN anyways. 

I'm not testing outside connections until I can get the internal one working.

I've rebooted apache and the server several times.

Is there any other setting that needs to be changed?

when I type in "netstat -tulpn | grep :8000"
my server says it is listening on 8000. so why wont my web browser go to 192.168.1.123:8000  ?


P.S. The only reason I'm going to the trouble of changing it is because my ISP is blocking port 80.

---

### Post by Arwen17evenstar on 2011-05-17
bump

I've tried changing the virtualhost stuff in ports.conf and 000-default to port 8000 too, but it doesn't fix it.

I'm able to connect to server through port 80 in a webbrowser. I'm able to ssh and sftp the server by port 22. So why can't port 8000 be made to work?

---

### Post by Arwen17evenstar on 2011-05-18
ok I feel like an idiot, hours and hours of thinking about it, I *finally* figured it out. My firewall was blocking the connection!

So I set Apache to Listen 8000 and namevirutalhost to 8000 in ports.conf
then I set virtualhost to 8000 in /sites-enabled/000-default
then I set shorewall to open up port 8000. and voila it works!

Hopefully that works for anyone with problems in the future.

---

