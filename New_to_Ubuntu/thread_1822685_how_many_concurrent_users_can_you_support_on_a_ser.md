---
title: "how many concurrent users can you support on a server?"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-10
I am trying to figure out, how many concurrent users can you support on a server?

possibly trying to figure out visitors, people logged in etc

how do you check that?

is it netstat -n? And then check for port 80?

I got maxclients 20 on apache2.conf, and keepalivetimeout at 2

?

---

### Post by ubudog on 2011-08-11
The amount of users the server can support depends on the power of the server.  If the server is super bulky, like Google's servers, then it can support millions upon millions of users at a time.  My server, a tiny little server, can probably support up to 1000 users, as long as they're not doing complex database operations.  

To find out how many users visit your site, you could use something
complex like Google Analytics, or a command like:
[http://www.geekpad.ca/blog/post/get-unique-visitors-from-apache-log-file](http://www.geekpad.ca/blog/post/get-unique-visitors-from-apache-log-file)

Hope that helps you,

Ubudog

---

### Post by 007casper on 2011-08-12
Thank you.  I already have analytics.  I just want to figure out the maximum capacity of the server per millisecond.

I found this on the net.  What do you think?
> ab -n 500 -c 10 [http://www.mydomain.com](http://www.mydomain.com)

I just want to make sure it is ok before I run it.

---

### Post by ubudog on 2011-08-13
Hmm, I haven't found anything on finding the maximum capacity per millisecond.  Where did you find that?

Also, when I run that against my server, I get:
```
ab: invalid URL

```

---

### Post by 007casper on 2011-08-14
:)  you need to replace the mydomain.com with a specific domain you want to test on the server.

before I run it on the server I want to make sure that command is good to go.  I dont want to run commands that I dont fully understand on the server.

ab -n 500 -c 10 is a bit strange to me.  I couldnt find much information on it.

---

### Post by ubudog on 2011-08-14
I did, I replaced mydomain with ubudog.net.  Where did you find that command?

---

### Post by georgemc on 2011-08-14
Your web server implementation and configuration will impose limits on how many concurrent connections/session/users the server can support.
 

 The ports or sockets available on systems these days, AFAIK, is 2^16 or 65536.  That would be the maximum number.  Now subtract from that the “well know” ports and services and the number is below 2^16.  So with all other resources being “infinite” your bottle neck will be the number of sockets/ports/connections any one box can have.  That is the mechanism how many DOS (Denial Of Service) attacks work, they continuously open  sockets/ports/connections and sit on them until all available  sockets/ports/connections are exhausted for that server and thus denying service.
 

 To get around this limitation, large volume web servers consist of multiple systems.  For example do a nslookup on “[www.goolge.com]("http://www.goolge.com/")” and you will see multiple IP address'.  Now when you query  again then you should notice that the order has changed.  They do a “round-robin”, or some other trick, to distribute the load across the multiple servers.
 

 All services usually and should move any incoming connections from their “well know” port to a free and available port.  For example when a connection request comes in on port 80 (HTTP) the server/service will move that connection to some other port.  This action frees up the HTTP port 80 for the next connection and so on.
 

 The “ab” command is part the “apache2-utils” package on my system.
 

 There is a lot of info on the Apache online documentation and you may want to look at the testing and mailing lists.  See the link below.
 

 Hope this helps.
 

 George
 

 Reference:
 [http://httpd.apache.org/test/](http://httpd.apache.org/test/)

---

### Post by HermanAB on 2011-08-14
Howdy,

As a rule of thumb for a present day garden variety machine, you could support 500 concurrent users per machine.

---

### Post by 007casper on 2011-08-20
thank you everyone.  Awesome info.

aptitude install apache-utils
ab -n 500 -c 10 [http://www.mydomain.com](http://www.mydomain.com)

see concurrent users

---

