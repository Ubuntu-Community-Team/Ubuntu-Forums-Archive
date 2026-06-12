---
title: "Networking information"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-06-17
Hi all,

I have a bit of a nagging curiosity, and I dont know where to get solid information about what Im trying to learn about.

I could certainly handle my own when it comes to Ubuntu and troubleshooting things on a single computer, but I have **absolutely** no clue when it comes to advanced networking. I have a few questions and I was wondering if anyone knew where I could find some resources to learn more or if you could explain them?


My main question is twofold; 
What is the main difference between a home server (IE one that is accessible from the local network for hosting things like videos or music) and a large server that Verizon would use to host all internet traffic from my home, for example. 

Following the same logic, How hard would it be to create a SERVER that would get us on the internet (without paying Verizon, for example) as well as, say, host a specific domain (tom@swartz.com anyone?)

If anyone has any advice, or maybe even reference material that I could read up on, I would be greatly appreciative!

Cheers!

---

### Post by JKyleOKC on 2010-06-17
> **tom.swartz07 said:**
> My main question is twofold; 
What is the main difference between a home server (IE one that is accessible from the local network for hosting things like videos or music) and a large server that Verizon would use to host all internet traffic from my home, for example. 

Following the same logic, How hard would it be to create a SERVER that would get us on the internet (without paying Verizon, for example) as well as, say, host a specific domain (tom@swartz.com anyone?)
The biggest differences between a home server and the equipment used by ISPs such as Verizon are (1) scale and (2) speed, both of which require hefty investments. I've been told, for instance, that a single card for a DSL RT (a concentrator that extends the range of the service) costs in the neighborhood of half a million dollars. The total investment for a small ISP is probably in at least 7, maybe 8, figures...

As for how hard it would be to set up your own domain server, the most immediate stumbling block (ignoring the scale and speed factors) would be in getting access to the "backbone" of the net. While AT&T is willing to install a really high-speed line for you, for only a few hundred thousand dollars of installation fees plus several thousand a month for its use, that's only the first step. You would also have to establish an account with a backbone service such as "Level One" (these are the companies that serve the ISPs such as AT&T and Verizon), and I would expect that to be only slightly less difficult than buying a Cadillac or Lincoln direct from the factory at dealer prices without going through a dealer.

In short, the only reason that our service prices are as small as they are is that the ISPs have spread their costs over thousands if not millions of customers!

You can, however, host your own domain from a home server; some ISPs require you to have a business account to do so while others don't care. You can also host it from a "web presence provider" which is what I do at a cost of less than $25/month. You can see the result at [http://www.jimkyle.com](http://www.jimkyle.com) and judge whether this approach would fill your desires (but of course, it does cost money).

---

### Post by tom.swartz07 on 2010-06-17
> **JKyleOKC said:**
> The biggest differences between a home server and the equipment used by ISPs such as Verizon are (1) scale and (2) speed, both of which require hefty investments. I've been told, for instance, that a single card for a DSL RT (a concentrator that extends the range of the service) costs in the neighborhood of half a million dollars. The total investment for a small ISP is probably in at least 7, maybe 8, figures...

As for how hard it would be to set up your own domain server, the most immediate stumbling block (ignoring the scale and speed factors) would be in getting access to the "backbone" of the net. While AT&T is willing to install a really high-speed line for you, for only a few hundred thousand dollars of installation fees plus several thousand a month for its use, that's only the first step. You would also have to establish an account with a backbone service such as "Level One" (these are the companies that serve the ISPs such as AT&T and Verizon), and I would expect that to be only slightly less difficult than buying a Cadillac or Lincoln direct from the factory at dealer prices without going through a dealer.

In short, the only reason that our service prices are as small as they are is that the ISPs have spread their costs over thousands if not millions of customers! 
Ah, I see.. Like I said, I really had no idea about any of it. Thanks for pointing that out.


> 
You can, however, host your own domain from a home server; some ISPs require you to have a business account to do so while others don't care. You can also host it from a "web presence provider" which is what I do at a cost of less than $25/month. You can see the result at [http://www.jimkyle.com](http://www.jimkyle.com) and judge whether this approach would fill your desires (but of course, it does cost money).

THAT is kinda what Im interested in. Do you have any advice/guides for going about this?

---

### Post by JKyleOKC on 2010-06-17
Google for "web presence provider" including the quotes, and you should get lots of hits. My provider is "CorpSite" and I've been with them for about 12 years. When I first signed up, their $21.95/month price was a real bargain, but now there are lots of lower-cost offerings, many below $10/month. You can register your domain name through most of these providers; mine is registered through GoDaddy and it costs less than $10/year. However, GoDaddy doesn't have the world's best reputation since many spammers and scam artists use their services...

---

### Post by elysianfields44 on 2010-06-17
In addition to what was said above, (and I hope I'm not misunderstanding your question), you might be interested in setting up a web server like Apache (i.e. accessible from anywhere in the world as long as you keep your port 80 open) which is both free and easy to do (I use it to share videos with friends who live out of town, and I've never paid for web hosting :-) The other advantage of running your own web server is that you can install any server-side technologies you wish to (usually web hosting providers charge you additionally for PHP, Python, databases etc). 

Furthermore, there are free DNS services which would provide you with a hostname of your choice (e.g. yourname.homedns.org) - admittedly it's not like having your own domain but if you only need this for sharing stuff with friends and not as an official website or anything then it's perfectly adequate (DynDNS provides an excellent free dynamic dns service - [www.dyndns.com](www.dyndns.com)).

Again, I hope I didn't misunderstand your question, and good luck!

---

### Post by tom.swartz07 on 2010-06-17
> **elysianfields44 said:**
> In addition to what was said above, (and I hope I'm not misunderstanding your question), you might be interested in setting up a web server like Apache (i.e. accessible from anywhere in the world as long as you keep your port 80 open) which is both free and easy to do (I use it to share videos with friends who live out of town, and I've never paid for web hosting :-) The other advantage of running your own web server is that you can install any server-side technologies you wish to (usually web hosting providers charge you additionally for PHP, Python, databases etc). 

Furthermore, there are free DNS services which would provide you with a hostname of your choice (e.g. yourname.homedns.org) - admittedly it's not like having your own domain but if you only need this for sharing stuff with friends and not as an official website or anything then it's perfectly adequate (DynDNS provides an excellent free dynamic dns service - [www.dyndns.com](www.dyndns.com)).

Again, I hope I didn't misunderstand your question, and good luck!

Nope, Thats exactly what I was asking for!

I already have DynDNS setup because I frequently use SSH while on the road, but Ive never quite figured out how to get an Apache server set up.

I have always heard about it, but I could never find a good 'introductory' guide to setting up an Apache server. Do you have any in mind?

---

### Post by wojox on 2010-06-17
Follow this how to [LAMP server installation]("http://ubuntuguide.org/wiki/Ubuntu:Lucid_tw#LAMP_server_installation")

---

### Post by tom.swartz07 on 2010-06-17
> **wojox said:**
> Follow this how to [LAMP server installation]("http://ubuntuguide.org/wiki/Ubuntu:Lucid_tw#LAMP_server_installation")

Great! Thanks!

Whats the difference between a full LAMP server and a simple Apache server?
(Sounds like the opening to a bad nerd joke....)

---

### Post by wojox on 2010-06-17
Lamp stands for Linux Apache Mysql Php

If you want to create a descent web page go with that.

---

### Post by elysianfields44 on 2010-06-17
> **tom.swartz07 said:**
> Whats the difference between a full LAMP server and a simple Apache server?

The other poster answered that, but to elaborate: if you install Apache alone, and then you decide you need a server-side scripting language (like PHP) and then a database (like MySQL) you will have to install those separately (and it's a bit of a hassle to set up all three to talk to each other, like you have to install some apache modules for php and mysql, and configure everything to work together). On the other hand, if you simply install a package like LAMP, that will install Apache, PHP and MySQL AND configure them to work together so they will work out of the box pretty much :) Also just to forwarn you, if you use LAMP it uses (what initially seem as) random directories (but they make sense after a while, though I do recall looking for them all over the place), for instance:

- to start apache: sudo /etc/init.d/apache2 start
- web-accessible files sit in: /var/www/
- main apache configuration file is: /etc/apache2/apache2.conf

Anyway, that's all you need to do really: put the files/web pages in your web directory (/var/www), start apache, and remember to setup your router to open port 80 (and keep dyndns running)! One other thing (once you have a grasp on running apache), is to ensure that the internal IP address of your computer stays the same, otherwise you might end up spending hours trying to figure out why you can't access it from outside :P 

I just did a quick search to find some helpful websites but most talk about installing apache, php and mysql separately (which really is harder) so I would recommend reading a book on apache (that's what I did). (I was in your position about a year ago and it can be a bit daunting to learn all about web server management, but it's a lot of fun!)

---

### Post by tom.swartz07 on 2010-06-17
> **elysianfields44 said:**
> The other poster answered that, but to elaborate: if you install Apache alone, and then you decide you need a server-side scripting language (like PHP) and then a database (like MySQL) you will have to install those separately (and it's a bit of a hassle to set up all three to talk to each other, like you have to install some apache modules for php and mysql, and configure everything to work together). On the other hand, if you simply install a package like LAMP, that will install Apache, PHP and MySQL AND configure them to work together so they will work out of the box pretty much :) Also just to forwarn you, if you use LAMP it uses (what initially seem as) random directories (but they make sense after a while, though I do recall looking for them all over the place), for instance:

- to start apache: sudo /etc/init.d/apache2 start
- web-accessible files sit in: /var/www/
- main apache configuration file is: /etc/apache2/apache2.conf

Anyway, that's all you need to do really: put the files/web pages in your web directory (/var/www), start apache, and remember to setup your router to open port 80 (and keep dyndns running)! One other thing (once you have a grasp on running apache), is to ensure that the internal IP address of your computer stays the same, otherwise you might end up spending hours trying to figure out why you can't access it from outside :P 

I just did a quick search to find some helpful websites but most talk about installing apache, php and mysql separately (which really is harder) so I would recommend reading a book on apache (that's what I did). (I was in your position about a year ago and it can be a bit daunting to learn all about web server management, but it's a lot of fun!)

Excellent! Thank you so much for the advice!
It is a little bit confusing to begin with, but I think Im getting the hang of it!

I have Apache and PHP installed, but I left off the SQL, I dont foresee any need for databases and stuff for what I hope to do.

Thanks again, everyone, for all of the advice! I appreciate it!

---

