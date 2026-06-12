---
title: "Making a web server on ubuntu desktop public"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by benseaver on 2009-11-09
I followed the steps on the following pages to set up an apache web server on ubuntu desktop:

[http://www.spoffle.com/technical/how-to-set-up-lamp-on-ubuntu-desktop-edition/](http://www.spoffle.com/technical/how-to-set-up-lamp-on-ubuntu-desktop-edition/)
[http://myy.helia.fi/~karte/install_apache_on_ubuntu.html]("http://myy.helia.fi/%7Ekarte/install_apache_on_ubuntu.html")

I can access the site from my LAN at work with no problem.  However if I try to access it from my house I cannot.  My ubuntu box is just plugged directly into a hub and there is no router directly attached. 

What steps would I need to take to be able to access the server from outside of work?

---

### Post by halitech on 2009-11-09
does your Ubuntu box have an external IP or an IP starting with 192.168? If you have an external IP, your ISP may be blocking port 80 which means you will need to run apache on another port. If its a 192.168.x.x then you need to configure the router/firewall computer to forward the port to the Ubuntu box.

---

### Post by The Funkbomb on 2009-11-09
While what the above poster said is true, you might not want to do that.

My ISP, according to a tech I spoke to, blocks port 80 specifically so you can't run a server out of your house.  By switching ports, you may still be in violation of your TOS.

---

### Post by benseaver on 2009-11-09
The IP address that I use to access the web server is: 172.30.x.x which  I got from running 
$ ip addr

---

### Post by halitech on 2009-11-09
> **benseaver said:**
> The IP address that I use to access the web server is: 172.30.x.x which  I got from running 
$ ip addr

as the FunkBomb stated, it may be against your ISP's TOS agreement so you may want to check with them. 

a 172.x IP address is also a non-routable IP so you need to configure your router/firewall box to forward the ports. If that address is actually being given to you by your ISP then they are using NAT addressing which means you probably won't be able to run a server on your system. Try going to [http://ipchicken.com](http://ipchicken.com) to see what your external IP address is.

---

### Post by benseaver on 2009-11-10
[SIZE=2][COLOR=Black]I get [/COLOR][/SIZE][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=5][COLOR=#0000ff][SIZE=2][COLOR=Black]209.7.x.x when I do the ipchicken site.  Not sure if that makes a difference or not.

Is it a common thing for people to run their own web servers?  I thought it but I feel like I'm wrong.[/COLOR][/SIZE][/COLOR][/SIZE][/FONT]
> **halitech said:**
> as the FunkBomb stated, it may be against your ISP's TOS agreement so you may want to check with them. 

a 172.x IP address is also a non-routable IP so you need to configure your router/firewall box to forward the ports. If that address is actually being given to you by your ISP then they are using NAT addressing which means you probably won't be able to run a server on your system. Try going to [http://ipchicken.com](http://ipchicken.com) to see what your external IP address is.

---

### Post by OffAxis on 2009-11-10
> I can access the site from my LAN at work with no problem. However if I try to access it from my house I cannot. My ubuntu box is just plugged directly into a hub and there is no router directly attached.
So the server is at work?

How do you 'Access the site from my LAN at work'?

While sitting at the server you should be able to reach your site from 
[http://localhost](http://localhost)
[http://127.0.0.1](http://127.0.0.1)

From your LAN computers you should be able to reach it at
http://<your local ip #, i.e. 172.x.x.x>

From ANY computer anywhere you should be able to reach your server at
http://<your external IP; 209.x.x.x>

> My ubuntu box is just plugged directly into a hub and there is no router directly attached. 
If you've got internet access from any computer on your LAN (more than one, right?) then you've got to have some sort of routing intermediary; a proxy server, a router, ...something.

---

### Post by wojox on 2009-11-10
It's common for people to run their own servers from home. Probably not a good idea to use the companies resources.

---

### Post by benseaver on 2009-11-11
Yes I will need to have IT configure something for me since I cannot access it from the 207.x address.  This is for a web development class at a school so they can upload to it (well that's a whole 'nother project) and see it from school and at home.

I guess I will ask about port forwarding.

---

### Post by OffAxis on 2009-11-11
http access typically runs on port 80 (so that's the one you'd forward for viewing the .html files)

For uploading files people usually use an ftp server, so you'd need to forward ports 20 and 21.

---

