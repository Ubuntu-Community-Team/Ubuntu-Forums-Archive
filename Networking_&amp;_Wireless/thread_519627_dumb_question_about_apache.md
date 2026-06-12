---
title: "dumb question about apache"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Richardinho on 2007-08-07
I know this is a dumb question so hopefully someone will answer quick, then it can all be forgotten about!

I've just installed apache on my system in the normal way from the reposittories, and have set it up so I can access my home web page using http:// localhost. This is to allow experimentation with PHP and Mysql.
I had the a similar set up on WindowsXP, and i've just migrated over to linux in the last few days.

So-Does setting up apache in this way allow people out there on the internet to somehow access my webpages on my system?

---

### Post by 505 on 2007-08-07
That depends. Are you behind a router, or do you have a direct IP address? Open a terminal and type 'ifconfig' and note your IP address. If you are behind a router, the IP normally starts with 192.168. People outside your homenetwork see only the IP address of the router. When they try to access it, the router (which is not running a web server) does not respond to the request.
On the other hand, if you have a IP address that is accessable from the internet, people can conntect to your computer using [http://123.123.1.2](http://123.123.1.2) (or whatever your address is).

You can also test this. Google for port scan and run the test. Note port 80, if it is open, the outside internet can conntect to you.

---

### Post by Richardinho on 2007-08-07
Not entirely sure how to run  a portscan;the programmes seem to be mainly for windows and I can't find any port scanner in synaptic. but i've looked up ifconfig, and my IP address indeeds starts with 192.168.. amd I am behind a router.

However looking in the apache2 folder in the ports.conf file, I see written 'listen 80' ( and not commented out either or anything) so, I'm not entirely sure now what's going on?

---

### Post by dreadlord_chris on 2007-08-07
> **Richardinho said:**
> I know this is a dumb question so hopefully someone will answer quick, then it can all be forgotten about!

I've just installed apache on my system in the normal way from the reposittories, and have set it up so I can access my home web page using http:// localhost. This is to allow experimentation with PHP and Mysql.
I had the a similar set up on WindowsXP, and i've just migrated over to linux in the last few days.

So-Does setting up apache in this way allow people out there on the internet to somehow access my webpages on my system?

I do believe that by default Apache listens on all interfaces - if you only want it to be accessible from localhost you need to configure it for that...

---

### Post by dreadlord_chris on 2007-08-07
> **Richardinho said:**
> Not entirely sure how to run  a portscan;the programmes seem to be mainly for windows and I can't find any port scanner in synaptic. but i've looked up ifconfig, and my IP address indeeds starts with 192.168.. amd I am behind a router.

However looking in the apache2 folder in the ports.conf file, I see written 'listen 80' ( and not commented out either or anything) so, I'm not entirely sure now what's going on?

that means Apache is *listening[* on port 80 of **all** interfaces - in your case your LAN IP (192.168...) and localhost (127.0.0.1). For Apache to be accessible from the Internet you would need to forward port 80 _from_ your router _to_ you LAN IP.

If you want Apache to be **only** listening on localhost then change the entry in _ports.conf_:
```

Listen 127.0.0.1:80

```
Save it, restart Apache

---

### Post by Richardinho on 2007-08-07
thanks Chris-

So essentially, all i need to do is change 'listen 80' to 'Listen 127.0.0.1:80' and then my website wont be able to be viewed over the net-although it probably wouldn't have anyway?

I don't want my site to be viewed over the net-not at this stage anyway! although I do intend further on down the line. (although I suspect I'll need a hardware upgrade too.)

---

### Post by dreadlord_chris on 2007-08-07
> **Richardinho said:**
> thanks Chris-

So essentially, all i need to do is change 'listen 80' to 'Listen 127.0.0.1:80' and then my website wont be able to be viewed over the net-although it probably wouldn't have anyway?

That is correct Sir... :KS

---

### Post by Richardinho on 2007-08-07
Thanks. :)

---

