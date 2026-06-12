---
title: "FQDN and IP address problem"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by john./ on 2007-11-08
Hi;

I'm stumped with this one - can anyone help?  I have a fixed IP address from my ISP, a draytech Vigor 2600plus router, and a terminal only installation of Ubuntu 7.04 on my server machine.

I have a sever getting its IP address by DHCP from my router - it happens to be 192.168.1.13 The router forwards port 80 for its ISP assigned fixed IP address to ...13

If I browse to my set up domain name, [http://www.whateveritis.co.uk](http://www.whateveritis.co.uk) the server returns the correct index.html file from the /var/www folder :-) BUT the location is shown as [http://my.fixed.ip.address/index.html](http://my.fixed.ip.address/index.html)

If I try to browse to [http://www.whateveritis.co.uk/weather/index.html](http://www.whateveritis.co.uk/weather/index.html) (which does exist) then the browser does 404. If I use [http://my.fixed.ip.address/weather/index.html](http://my.fixed.ip.address/weather/index.html) the weather page shows nicely.

What did I do wrong? - Or, where should I start looking for a fix? The /var/log/appache2/error file shows no related messages.. even when log level is debug.

Thank you for any pointers at the cause;

john./

john./

---

### Post by niobos on 2007-11-08
Since you got the [http://blablabla/](http://blablabla/) to work, it seams that your router-forwarding is working correctly. ALso, since you're getting an 404, you must have hit SOME server rejecting you.
I'm not sure how you managed to map a FQDN to your IP. Is it a true DNS? or is it a web-forwarding service?
From the information you gave, I'm guessing it's that last category. In that case it's not that abnormal that it doesn't work. since they'd have to explicitly configure their forwarding service to rewrite the path as well.

---

### Post by john./ on 2007-11-08
Hi;

thanks for the reponse; made me think a bit.

Yes, the domain is in fact forwarded to my machine. The problem is comming to light as I am setting up a second domain which is to point to a sub folder.

Perhaps I shall explore setting up virtualisation. However I am still worried as the FQDN is re-written in the browser's address bar to show the IP numbers - not very attractive and may react on zone alert etc...

hmmm - still pondering this!

john./

---

### Post by niobos on 2007-11-09
I think using a true (dynamic) DNS will give you what you want. The URL will stay what you want.
For the second domain, just setup vhosts in apache and you have effectively 2 completely seperate websites.

---

