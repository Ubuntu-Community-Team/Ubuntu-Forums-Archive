---
title: "need help setting a home website using apache webserver"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by arun chauhan on 2009-12-01
[FONT=Times New Roman][B]Hi guys, i have already registered with dyndns.com and have got domain name. i have my ddclient running. my router supports the dynamic dns and i have configured my router to have the name of my site. i have apache running..... but still can't access my site from outside the network..... 
When i type the site url on my home network systems the router page pops up......

A few things that i have discovered are that my apache  web server httpd.conf file shows nothing. that is when ever i open it, i don't see any directives written, in fact just a cursor blinks at the top left corner and the whole page is blank.....

and if my router supports dynamic dns do i have to port forward......
 please help me..... It's been one month and i am still clueless......[/B]

**Thanks in advance....**[/FONT]

---

### Post by t0p on 2009-12-01
> **arun chauhan said:**
> [FONT=Times New Roman][B]
and if my router supports dynamic dns do i have to port forward......
 [/B][/FONT]

If you're just getting your router's page when you point a browser at your site's url, then I'd say yes, you do need to port forward.

---

### Post by teward on 2009-12-01
Even if its not dynamic DNS, you'd still need to set port forwarding, since routers don't like servers on them unless you configure them to allow it to work (hence the port forwarding).  Make sure you configure port 80 on port forwarding.  But be warned:  This opens your computer/server to hackers and malicious attacks, even if it IS Linux and not Windows/Mac/otherOpSys.

---

### Post by arun chauhan on 2009-12-01
[B]Ok i will port forward and see, but are there any changes regarding the apache configuration files........ Because i think we need to name server on the name of our site...... or something like that....
if there are any, can you please tell me what all are those changes and how to do them.....  
Thanks......[/B]

---

### Post by bodhi.zazen on 2009-12-01
This link should get you started :

[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP") 

Are you getting a specific error message ?

---

### Post by arun chauhan on 2009-12-02
[B]Thanks for the link.... when i am trying it out on the proxy server
[http://www.freeproxyserver.net/](http://www.freeproxyserver.net/)  
I am getting the error message
[/B][B]Error: 110: Connection timed out (URL: arunchauahan.dyndns.org)
What does that mean? i mean is the proxy server able to access my site and the connectiion is getting timed out or some thing else?????

Thanks again.....[/B]

---

### Post by arun chauhan on 2009-12-02
> **bodhi.zazen said:**
> This link should get you started :

[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP") 

Are you getting a specific error message ?



**yes from a computer outside my network i am getting a error message of page broken.....**

---

### Post by ukripper on 2009-12-02
what ports you forwarded on your router?

---

### Post by arun chauhan on 2009-12-02
port 80 i think......

---

### Post by bodhi.zazen on 2009-12-02
You should be able to connect by entering your public IP address in your firefox browser.

If that is not working, what error message do you get ? Most likely your porblem woudl be with Port Forwarding.

If it is working, then you need a DNS service, there are several that are free such as DynDNS.

---

