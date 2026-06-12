---
title: "Apache help"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by kulkarniniraj on 2008-10-24
Hi
   I have been using apache under windows now I want to use it under ubuntu 7.10
Now in windows there is a folder named htdocs where i can put my files & access them through localhost syntax. I dont know where i have to put files in ubuntu. Also can i create virtual directories?

     Another question, I want set up web server behind router (something called virtual server) .When i go to my router(adsl modem) config page it asks me following parameters can anyone explain its meaning

NAT -- Virtual Servers Setup

Virtual Server allows you to direct incoming traffic from WAN side (identified by Protocol and External port) to the Internal server with private IP address on the LAN side. The Internal port is required only if the external port needs to be converted to a different port number used by the server on the LAN side. A maximum 32 entries can be configured.



1 Server Name 	
2 External Port Start 	
3 External Port End 	 
4 Protocol 
5 Internal Port Start 	
6 Internal Port End 	
7 Server IP Address 	
8 Remove


please help

---

### Post by Coreigh on 2008-10-24
I am running 7.10 and my default htdocs folder is /var/www. Any web documents put in that folder will be available by a browser. One note if you do not have an index.html page then you need to type the full address with pagename ([http://mywebaddress/pagename.html/](http://mywebaddress/pagename.html/)) Or configure Apache to a llow directory browsing.
You can create subdirectories in the www folder and access them directly ([http://mywebaddress/subdirectory/pagename.html/](http://mywebaddress/subdirectory/pagename.html/)) or create virtual directories by editing the config file in /etc/apache2/sites-available using the <virtualhost> directive.

This how to is OK but there are many out there, Google for: "Configure Apache2 Ubuntu"

[http://wowtutorial.org/en/node/24](http://wowtutorial.org/en/node/24)

I am afraid I can't help with the router. I do know it is fairly straight forward but I have never had to do it my self. I'd start with Google; "configure NAT *your-router*"

I hope this get you on your way.

---

### Post by Iowan on 2008-10-24
I found [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") page helpful.  [Here]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100") is another, though I haven't read it (yet).

---

### Post by Sarmacid on 2008-10-24
I'm not sure if this is the correct way to set up NAT, but I guess it's worth a try


1 Server Name(The name of the machine with Apache)
2 External Port Start(80)
3 External Port End(80)
4 Protocol(tcp)
5 Internal Port Start(80)
6 Internal Port End(80)
7 Server IP Address(The internal ip of your server)

> Virtual Server allows you to direct incoming traffic from WAN side (identified by Protocol and External port) to the Internal server with private IP address on the LAN side. The Internal port is required only if the external port needs to be converted to a different port number used by the server on the LAN side. A maximum 32 entries can be configured.

When you're behind a router, you only have one public ip, but you might have several private ones, so for the router to know where to send new incoming traffic, you have to set up NAT.

Hope this helped!

---

