---
title: "How to set up apache on LAN?"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by z3r0-c0d3r on 2006-08-26
I installed apache2 but I don't know how to access the computer with apache from a client because I don't know the ip address. My network has 2 computers on it currently and it's connected through a adsl modem/router which has a dynamic ip address which changes everytime i connect. When i go to whatismyip.com and get my ip address and try to connect with the ip i get i go back to my routers config screen. So is there a way for me to find out my servers ip address?

Thanks

---

### Post by reacocard on 2006-08-26
If i understand correctly, you're tring to access the apache server from the Internet through the router? You'll need to tell the router to pass port 80 through to the machine with the server on it.

---

### Post by az on 2006-08-26
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by tturrisi on 2006-08-26
If you are in the US then chances are that your isp is filtering port 80, thus you won't be able to connect to apache using your real ip address.  However, you can config your router to forward port 80 requests to another port such as 8080 or 8081.  You will also have to config apache to listen to port 8080.  This is done by adding a line in /etc/apache2/ports.conf
```
Listen 80
Listen 8080
```

You can ALWAYS access apache using port 80 from any computer on your lan by typing in a browser address bar the following:
[http://192.168.x.x](http://192.168.x.x)  (address of comp apache is installed on)

You can access appache on the comp it is installed on by typing: [http://localhost/](http://localhost/)

For best results, use a static ip for the comp that apache is installed on.

---

### Post by z3r0-c0d3r on 2006-08-27
I only want to access the computer on LAN. I think the problem is the machine wont let the other computers access it because when i type the computers static address (which is 10.0.0.14) i get the apache screen thing, but wen i try from a different computer it says can't access. How do I make the machine allow others machines to acces it??

---

### Post by tturrisi on 2006-08-27
[http://10.0.0.14:80](http://10.0.0.14:80)

---

