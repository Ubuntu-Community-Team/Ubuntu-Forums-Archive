---
title: "Ubuntu Server external web access"
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by okeefem2 on 2015-01-10
Hello all!

I have been working on setting up a home server using ubuntu server 14.04 to host a Word Press based website for a friends photography business, using apache2.

So far I have it set up so I can ssh into it locally and can access both the website and the wp dashboard on my web browser locally.

However I cannot access it at all outside of my home network. 

I have port forwarding set up for both port 22 (for ssh) and for 80 (web sharing)

It seems like connections are getting to the server because, while having someone attempt to access the webpage the output of *sudo netstat -napW* 

gives me:

tcp6       0      0 10.0.*.*:80            10.0.*.*:52513          TIME_WAIT   -  

and nothing happens, eventually it times out and says the server is not responding.

I have been searching the internet for a few days now and have found lots of helpful insight into others problems that are, alas, not working for me.

Possibly useful information: I use an airport express router and have set up a static IP for the server.

Any help would be appreciated, and please do not hesitate to ask for more info.

---

### Post by TheFu on 2015-01-11
Does your ISP allow servers? Many will block inbound connections.  Also, if the ISP is doing double NAT, there isn't anyway to do what you want.  What is the public IP ?

---

### Post by okeefem2 on 2015-01-11
Ahhh yes I believe that was the problem, my ISP says in its acceptable use policy that web servers are not allowed. Thank you for that, I guess Im moving the server to mom's! haha

---

### Post by TheFu on 2015-01-11
For a personal server, I don't think ISPs care.  Just put the service on a different port - perhaps 50080?
Of course, for a real, commercial, webserver, you really need to be hosted at a service provider.

BTW, that netstat shows only ipv6, not ipv4, so your webserver doesn't seem to be properly configured. Some content systems only listen on 127.0.0.1 by default and you need to tell them to listen on all IPs.  I don't use those, so don't know.

And double-NAT is still a question.

Lastly, check out this link concerning php security:  [http://blog.ircmaxell.com/2014/12/php-install-statistics.html](http://blog.ircmaxell.com/2014/12/php-install-statistics.html)
Please don't become like most other php websites. Stay patched.

---

