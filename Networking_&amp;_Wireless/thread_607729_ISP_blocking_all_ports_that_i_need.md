---
title: "ISP blocking all ports that i need"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by tbuzz2 on 2007-11-09
Total noob question.... My isp is blocking SSH(port 22) and web server(port 80) how do you get around your isp blocking ports with port forwarding if possible can someone give me a breakdown of how to do this PLEASE!!! im new to ubuntu and have been trying to get to my web server remotely for 2 weeks and cant do it myself I NEED HELP PLEASE!!!

---

### Post by stalker145 on 2007-11-09
> **tbuzz2 said:**
> Total noob question.... My isp is blocking SSH(port 22) and web server(port 80) how do you get around your isp blocking ports with port forwarding if possible can someone give me a breakdown of how to do this PLEASE!!! im new to ubuntu and have been trying to get to my web server remotely for 2 weeks and cant do it myself I NEED HELP PLEASE!!!

In your /etc/ssh/sshd_config file, find the section where it says > # What ports, IPs and protocols we listen for
Port 22 and change it to a port that you can actually use. After that, you should be able to SSH into your server by using the string > ssh xxx.xxx.xxx.xxx:port where port is the number you chose.

In your /etc/apache2/ports.conf file, change the section that says > Listen *:80 to something that you can actually use. After that, you should be able to access your web server by using the string > [www.yourdomainname.com:port](www.yourdomainname.com:port) where port is the number you chose.

Ensure that once these changes are made, you restart your respective servers and place the changes into your router's port forwarding.

Possible HTTP ports can be 81, 8080, or anything not being used by some other program. As for suggestions on SSH... dunno... someone else might know some other ports for that one.

EDIT: The :p face is actually a colon followed by a lower case "p" (or : p without the space). Dang smileys ;)

---

### Post by tbuzz2 on 2007-11-09
Thanks stalker145 as soon as i get home from work i will give it a try THANKS for your help!!

---

### Post by sputnick on 2008-06-11
hi, anyone know how i can get the server to read my 

/etc/ssh/sshd_config

file without rebooting it? i have 15,000 users on the server...

---

### Post by Rhubarb on 2008-06-11
> **sputnick said:**
> hi, anyone know how i can get the server to read my 
/etc/ssh/sshd_config
file without rebooting it? i have 15,000 users on the server...
Try this:
```
sudo /etc/init.d/sshd restart
```
Just remember, it will disconnect anyone that's logged into your ssh server.
It shouldn't effect your users logged in to apache web server at all.

---

