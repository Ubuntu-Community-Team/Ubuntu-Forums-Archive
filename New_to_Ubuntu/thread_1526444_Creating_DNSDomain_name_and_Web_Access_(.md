---
title: "Creating DNS/Domain name and Web Access :("
date: 2010-07-08
forum: New to Ubuntu
---

### Post by reydempto on 2010-07-08
Okay. I literally just stayed up all night long installing/configuring Ubuntu Server Edition using this handy guide.

Pretty in-depth guide. The first time around I was careless and skipped a step or two, resulting in me having to start over from step one. So I reinstalled Ubuntu Server 10.04, and followed the guide to the letter. This time it went perfectly (I even installed the gnome desktop that I love so much), except for a couple things that I hope you can help me with.

I am no stranger to linux, and I also know how to admin a website. I've bought hosting/domains before, and etc. From what I THINK I understand, I am able to create my own DNS, and thus my own domain name, such as "imadethisdomain.com", hosted on my shiny new server. Am I correct?

So that's problem number one: I need a DNS so I can have my own domain (without having to resort to buying one)

Problem Number 2: I can only access my 'site' (/var/www) via my local network. Basically on any of my 3 computers around the house I am able to type "192.168.0.240" into a browser and /var/www/index.html will show, confirming that I have done everything right locally speaking.


So how do I

a) make my own domain name/DNS

and

b) make that domain accessible outside my home network (I plan on hosting a small forum to archive some live concerts)



I've spent hours tonight attempting to configure bind9, ispconfig, phpmyadmin, mysql, and my router's port forwarding/DMZ functions, all to no avail. I have read countless tutorials and 'guides' in broken English from all over the internet, and I am at my wit's end!

If you need any more info from me, let me know.

---

### Post by ubudog on 2010-07-08
Check this out:[http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

It's what I used for my site (below).

---

### Post by reydempto on 2010-07-08
Interesting link, thanks! Does this mean that I cannot create my own DNS nameserver? I thought that I would be able to basically create my own dot com.

---

### Post by reydempto on 2010-07-08
O....kayyyy...thanks.

---

### Post by reydempto on 2010-07-08
> **ubudog said:**
> Check this out:[http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

It's what I used for my site (below).

Okay so I followed the guide, and also the advice in the 5 pages afterwards. I am only more confused.

When I go to my new domain, i get propted for a password, and NONE of my usernames or passwords fit. I think its because on dyndns I used my outside (ISP) IP address...am I right? If I go to my ISP's ip that I used, I get the same password prompt. So I think I am doing something wrong. This is the password prompt for my ISP's technicians I believe. I am obviously doing this wrong. I have dyndns pointing to the IP I get from whatismyip.com. Also, I would like to add that when not connected locally, the dyndns domain comes up as dead, no ISP technician password prompt :P....so not only does it not point correctly, it also doesn't even point outside the local network.

SOMEONE PLEASE HELP! I have gotten no sleep and this is driving me insane!

---

### Post by ubudog on 2010-07-08
This didn't happen to me.  I will call in an expert.

---

### Post by bodhi.zazen on 2010-07-08
You need to do two things.

First you need to purchase a domain name. They are not *that* expensive.

If you do not want to purchase a domain, you can register for any of the free services

[http://www.dyndns.com/](http://www.dyndns.com/)

The free services work fine, but your choice of domain names is more limited.

You can run bind, and that will work on your LAN, but not outside of your LAN. If you think about it, that makes sense, otherwise anyone could simply set up a BIND server and become google.com or bank.com or ...

Well , you get the idea. for what you want, forget about running a DNS server (bind).

Next you need to forward port 80 from your router to your web server. Once you do that you should see your index page when you put your public ip address into the firefox address bar, same as when you use the IP on your LAN (I am assuming you know the difference between a public and private IP address ? ).

Once you have done these things ^^ you need to wait for the DNS to propagate, wait 24 hours. If after 24 hours you can not connect using your domain name, contact your dns provider.

---

