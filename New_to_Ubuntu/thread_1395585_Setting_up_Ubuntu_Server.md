---
title: "Setting up Ubuntu Server"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Gh-x on 2010-02-01
Hi,

To begin with i am absolute beginner in linux moreover with linux server, but due to my need i need to learn how to manage linux server for future use. That is when i though to begin my journey with ubuntu server.

I have an old computer:
Intel Celeron 2.6 socket 478
80GB of Hard Drive
and unknown motherboard.

Now at home i have connection of 2Mbit downlink and 512KB uplink. 
The line is connecting 1 notebook,1 PC (my main dekstop running windows 7) and the ubuntu server which i connect using router. Furthermore i have an dynamic ip address that change each time i reconnect to the internet. 

The Ubuntu server will be used as a webserver for now, as i have project to customize joomla before uploading it to a proper webhosting and built up other web based aplication. 

At the same time, i need to manage this server through ssh as it will be experience for me before buying a dedicated server later on. 

The server should also needed to be access from the internet as my friend will be working on it too.

It seem like to turn into an essay ;D

Anyway, i am hoping the community of ubuntu could help me to setup my server, and lead me to understand it and manage it better.

Thank you

---

### Post by Gh-x on 2010-02-01
[IMG]http://img196.imageshack.us/img196/4050/14192102.png[/IMG]

to begin with here is a problem,

i have 80 gb of disk, if i were to 30gb in the above section then there will be remaining 50gb. The question is how can i use the remaining 50gb?

-this might be a really low level question, but i would like to know.

P.S: sorry for my bad english.

---

### Post by pavel989 on 2010-02-01
50gb can be used to encrypt your own data that youd like to be able to access from the server. or you can install more kool things like a cloud server, a streaming server, ftp server, etc. check out the package manager, lots of kool things

---

### Post by tornado42 on 2010-02-01
check this out... I followed these instructions and everything is working...
 
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

---

### Post by Gh-x on 2010-02-01
> **pavel989 said:**
> 50gb can be used to encrypt your own data that youd like to be able to access from the server. or you can install more kool things like a cloud server, a streaming server, ftp server, etc. check out the package manager, lots of kool things

Hmm does that mean, if i want to put my website file, it should be placed on the remaining 50GB? 
how can i partition it?

> **tornado42 said:**
> check this out... I followed these instructions and everything is working...
 
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

Thanks i will check it out.

---

### Post by pavel989 on 2010-02-02
> **Gh-x said:**
> Hmm does that mean, if i want to put my website file, it should be placed on the remaining 50GB? 
how can i partition it?


not necessarily, but you can. and when you install a server you can partition your drive, its pretty straight forward. simply select "guided partitioning" or something along the lines of guided

---

### Post by samantha_ on 2010-02-02
> **Gh-x said:**
> Hi,

To begin with i am absolute beginner in linux moreover with linux server, but due to my need i need to learn how to manage linux server for future use. That is when i though to begin my journey with ubuntu server.

I have an old computer:
Intel Celeron 2.6 socket 478
80GB of Hard Drive
and unknown motherboard.

Now at home i have connection of 2Mbit downlink and 512KB uplink. 
The line is connecting 1 notebook,1 PC (my main dekstop running windows 7) and the ubuntu server which i connect using router. Furthermore i have an dynamic ip address that change each time i reconnect to the internet. 

The Ubuntu server will be used as a webserver for now, as i have project to customize joomla before uploading it to a proper webhosting and built up other web based aplication. 

At the same time, i need to manage this server through ssh as it will be experience for me before buying a dedicated server later on. 

The server should also needed to be access from the internet as my friend will be working on it too.

It seem like to turn into an essay ;D

Anyway, i am hoping the community of ubuntu could help me to setup my server, and lead me to understand it and manage it better.

Thank you

You will have to forward the ports you want to access from the internet through your router. If you have DMZ, you can simply use that.

For the Dynamic IP Address, I reccomend you use DynDNS + ddclient; [http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html)

---

### Post by superprash2003 on 2010-02-02
thats right you need to open ports to access it over the internet.. for your web server you need port 80 to be opened ( apache ) and for ssh you need port 22 open..

---

