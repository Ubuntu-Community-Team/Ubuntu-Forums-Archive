---
title: "changed apache default port but url not showing"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by byenary on 2009-03-06
Hello,

i have added Listen 8080 to ports.conf when i browse to the ip
192.168.123.37 -> it gives met the IT WORKS index.html
If i go to 192.168.123.37:8080 I get a not found but it displays following line 
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at 192.168.123.37 Port 8080
Does he looks somewhere else for the html when using an other port?
I did not change a thing, it is a clean ubuntu 8.10 install

Thx in advance!

---

### Post by Hospadar on 2009-03-06
You probably just need to change the port in the virtualhost.
If you edit /etc/apache2/sites-enabled/default and up right at the top you'll see something like "VirtualHost *:80" if you change that port number and restart apache it should work.

There's a little more detailed note on this if you read the comments in ports.conf I believe.

If you're curious what a virtual host is, it lets you host multiple domain names with the same apache.  The consequence is sometimes like this it requires a little extra fiddling.

---

### Post by byenary on 2009-03-06
thats correct, should have read the comments in ports.conf...its pretty clear :P

---

