---
title: "Apache Tutorial"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by joec369 on 2009-04-19
I am looking for a very basic Apache Tutorial.  I have it installed but I am having trouble getting my website to work.  I looking for a simple tutorial.  I don't need virtual hosts or directives or whatever.  Just something that will help me put up a simple text web page on my LAN.

Thanks

---

### Post by theozzlives on 2009-04-19
The Ubuntu Linux Bible can do that.

---

### Post by joec369 on 2009-04-19
Thanks I'll look it up

---

### Post by seekerofknowledge on 2009-04-19
At what point are you?

---

### Post by ibuclaw on 2009-04-19
In a nutshell, you run:
```
sudo tasksel install lamp-server
```
To setup the initial Apache/MySQL/PHP server.

Then setup your firewall as appropriate (allow port 80), and then setup the ownership on the webserver files directory.
```
sudo chown -R $USER:admin /var/www
```
Note: use only for non-production web servers - this is not the most secure way to do things.

Then update the index.html and other files in /var/www as fits your website design/intention, then open up a web browser and type in:
```
http://localhost
```
To view it from your own computer, or use the IP address of your computer on the network to view it from another computer on you network.

If you do not wish for people/computers to connect to your webserver from outside of your network, you do not need to port forward on your router.

Regards
Iain

---

