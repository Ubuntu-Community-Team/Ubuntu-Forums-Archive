---
title: "want to learn php, sql. What do i need?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by kapi on 2009-02-12
Hi have been on the w3cschools to see about using php. previously I was learning asp.net but I want to learn php. I have ubuntu ibex intrepid and want to know what I install for web development. 

w3schools talks about setting up a server on your own machine, I'm not going to run my own server but am I required to install the same software so I can code on my own machine? I had iis installed in windows before I moved to linux, am a bit unsure what steps to take. any help would be grateful.

Thanks 

kapi
long live the linux revolution :-)

---

### Post by superprash2003 on 2009-02-12
you could install LAMP which includes apache and php.. and you could make it a local server so only you could acess..

---

### Post by kapi on 2009-02-12
great thanks, I was wondering what the best option was. other users have also mentioned using XAMPP. So is there a best option - which one is the most appropriate one?

thank you again

Kapi

---

### Post by prometheus1981 on 2009-02-12
> **kapi said:**
> great thanks, I was wondering what the best option was. other users have also mentioned using XAMPP. So is there a best option - which one is the most appropriate one?

thank you again

Kapi

XAMPP is free and extremely easy to setup. I would install it on a computer that's connected to the network but not the one you use (if possible), this way it will not get in the way with your normal PC usage.

Also, if you are interested in php and sql for web developing, go to the web developer's handbook website ([http://www.alvit.de/handbook/](http://www.alvit.de/handbook/)).

---

### Post by mcduck on 2009-02-12
LAMP is also very easy to setup in Ubuntu, and since it's the same packages that are used on Ubuntu servers you'll get automatic security updates etc, and the server integrates better with the rest of the system.

To install LAMP you actually only need to run a single command:
```

sudo tasksel install lamp-server
```
(or you can open Synaptic Packge Manager, go to Edit/MArk Packages by Task, mark "LAMP server" and then click "Apply" in Synaptic to install everything.) Either way, that's actually easier than downloading and extracting XAMPP by hand. ;)

You may want to install some graphical interface for MySQL as well, for that I recommend phpmyadmin. It's also available in ubuntu's repositories..

---

