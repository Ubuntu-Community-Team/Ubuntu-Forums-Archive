---
title: "Localhost overruling?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Nerflander on 2011-03-02
Hi there !

ive got a webshop on my server. Now thats in the var/www.

so lets make that:

var/www/webshop1  
Webshop 1 is running perfect.. Now i made a second webshop

var/www/webshop2

now if i go to my browser and go to xxx.xxx.xx.xx/webshop2 it goes to xxx.xxx.xx.xx/webshop1

anyone know why this is getting overruled to the first webshop?

thanks in advance

---

### Post by Nerflander on 2011-03-02
anyone?

---

### Post by Mariane on 2011-03-02
I don't know what a webshop is. But I gather by xx.xx.xx.xx you mean your 2 pages have the same IP? If so, I would suggest adding an html file called "index.html" in each webshop directory and then checking your apache settings. 

I couldn't guide you through that but I know that when apache2 has to serve different files depending upon the domain name (if you have more than one on the same IP) it has to be configured specifically, it doesn't do it by default. 

Mariane

---

### Post by augustuen on 2011-03-02
It seems like you have to set up Apache to recognize which webshop you are trying to reach. By default Apache is set up to listen to every incoming connection on port 80, and then send it to the /var/www directory. You have to set up a second site, and then set each of them to use either the external IP or the internal IP. If you have a DNS server, I think that you can use it to set up a fake domain (like webshop1.example.com and webshop2.example.com) and then set up Apache to listen for a connection through these domains.

---

### Post by Nerflander on 2011-03-09
Il try the host file. 

For further information their 2 magento webshops. Same IP but different folder in the var/www/

So what i mean is normally it doesnt really matter and it would show you the websites you adress.

---

