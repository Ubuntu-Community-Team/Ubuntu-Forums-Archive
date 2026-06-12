---
title: "Configuring a reverse proxy to work remotely on other machine"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by fdd2 on 2014-08-06
Hi, I need your help to configure my connection to another machine.

On the remote machine, I work on localhost using ServerNames.
On the current machine, I want to access to the local web pages of the remote machine.

In my /etc/hosts, I have :

24.???.???.??? remotehost
127.0.0.2 servername1

In my sites-available config, I have :

> <VirtualHost 127.0.0.2:80>
    ServerName servername1
    ProxyRequests Off

    ProxyPass        / [http://remotehost:8080/](http://remotehost:8080/) retry=0
    ProxyPassReverse / [http://remotehost:8080/](http://remotehost:8080/)
</VirtualHost>

<Proxy *>
 Order allow,deny
 Allow from all
</Proxy>

I put 8080 as the port because nmap told me it was an open port for this host. 
When I put servername1 in my address bar, I get a blank page and firebug tells me that it got an error 500 : internal server error.

I enabled the modules proxy, proxy_http.

I guess it is a port problem, but I really don't know how to fix it.

Thanks for your help!

---

### Post by sedawk on 2014-08-06
So you have a httpd (apache) daemon running on "current machine" and you start firefox on "current machine" and then try URL 127.0.0.2[:80] ?
Then, because of sites-available.config your local httpd daemon on "current machine" is forwarding your request to remotehost:8080.

Question is: what is running on remotehost:8080? You say the port is open in nmap, so isn't there another service already runnng on 8080?
Did you start httpd on "remotehost" to listen to port 8080, because that is what would be required`
If you run firefox on "current machine" where httpd is running, then firefox on that machine must also work with URL "remotehost:8080".
If firefox on "current machine" cannot handle URL "remotehost:8080" properly, you httpd on the same machine will also fail ...

---

