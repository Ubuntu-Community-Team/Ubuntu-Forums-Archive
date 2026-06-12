---
title: "cant find software"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by mick_86 on 2011-04-02
just downloaded and isntalled wordpress but its not appeared in my applications menu, how can i put it there?

---

### Post by wojox on 2011-04-02
Wordpress needs to be run on a web server like Apache. You need to set that up and link it to /var/www/

---

### Post by mick_86 on 2011-04-02
> **wojox said:**
> Wordpress needs to be run on a web server like Apache. You need to set that up and link it to /var/www/

ok, do you know of any software that is free to download so that i can create a website offline then upload it?

---

### Post by Daniel0108 on 2011-04-02
> **mick_86 said:**
> ok, do you know of any software that is free to download so that i can create a website offline then upload it?

Install apache, if you don't forward a port, it won't be online:
sudo apt-get install apache2

After installing apache, you need php and mysql.

There's a program called LAMP, it's not really good for online web-servers, but it's easy and okay for offline testing. LAMP automatically installs Apache, FTP, PHP and MySQL.

After you installed apache2/LAMP, open a browser and go to "localhost" or "127.0.0.1".

I hope this helped you,
Daniel

---

### Post by Paqman on 2011-04-02
> **mick_86 said:**
> ok, do you know of any software that is free to download so that i can create a website offline then upload it?

What exactly are you trying to do? Do you want to learn how to build sites from scratch, or do you just want to get something out there? Wordpress offer free hosted blogs on their site, all you need to do is register and they'll set it all up for you.

---

### Post by mick_86 on 2011-04-03
> **Paqman said:**
> What exactly are you trying to do? Do you want to learn how to build sites from scratch, or do you just want to get something out there? Wordpress offer free hosted blogs on their site, all you need to do is register and they'll set it all up for you.

trying to learn, i know there is plenty of sites that will let me build using there software and its easy but thats not what i want.

---

