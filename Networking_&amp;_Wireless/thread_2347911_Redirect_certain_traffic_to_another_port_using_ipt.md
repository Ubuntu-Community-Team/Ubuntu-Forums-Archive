---
title: "Redirect certain traffic to another port using iptables?"
date: 2016-12-29
forum: Networking &amp; Wireless
---

### Post by joshuaa001 on 2016-12-29
Hello.

I am running a web server and i have a list of ips that are currently being DROPPED in iptables. I would like to notify those IPs whenever they try to access my webserver, that they have been blocked. 

After speding the entire day googling around, i've found a solution to be like this:

- create a virtual host in apache on different port (192.168.100.2:63) and put a warning-your-ip-has-been-blocked html page there
- redirect traffic using iptables to that port.

Now, i have found various variations of the iptables command, such as

[COLOR=#000000][FONT=Verdana]iptables -t nat -A PREROUTING -i eth0 -s ip.i.want.to.block -p tcp --dport 80 -j REDIRECT --to 63


[/FONT][/COLOR] but i'm not sure if this is correctly used. moreover, my firewall ip list also contains ip ranges, how to redirect those as well?

If someone could write an iptables example, i would be forever grateful :)

Thank you and Happy New Year to everybody!

---

### Post by TheFu on 2016-12-30
Don't know off the top of my head how to do it with iptables.

I use a reverse proxy for this. IP ranges (and other "bad clients") get a 403 error - denied. The reverse proxy, nginx, handles the error. I wouldn't want these "bad guys" having access to the same process running my different websites. I know this works:
[https://www.cyberciti.biz/faq/nginx-redirect-backend-traffic-based-upon-client-ip-address/](https://www.cyberciti.biz/faq/nginx-redirect-backend-traffic-based-upon-client-ip-address/)

Honestly, I'd just stay with your current DROP method. Don't waste any more bandwidth than necessary.

---

### Post by The Cog on 2016-12-30
Use a separate line for each address/range, just as you do now with your DROP commands.
```
iptables -t nat -A PREROUTING -i eth0 -s 1.1.1.1 -p tcp --dport 80 -j REDIRECT --to 63
iptables -t nat -A PREROUTING -i eth0 -s 2.2.2.2 -p tcp --dport 80 -j REDIRECT --to 63
iptables -t nat -A PREROUTING -i eth0 -s 3.0.0.0/8 -p tcp --dport 80 -j REDIRECT --to 63
```

I like the idea of using a really simple single-threaded static web page server for this, something that can't be abused to use up all your CPU or compromised by the bad guys.
It may be worth looking at rate limiting the number of connections per second to this server (google iptables rate limit).

---

### Post by TheFu on 2016-12-30
With lots and lots of rules, use **ipset** instead.  10,000x faster.
[http://manpages.ubuntu.com/manpages/xenial/man8/ipset.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/ipset.8.html)
[https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset](https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset)

---

