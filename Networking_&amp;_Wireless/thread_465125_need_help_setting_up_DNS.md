---
title: "need help setting up DNS"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by klejnieks on 2007-06-05
Ive tried searching and doing some of the things suggested on the boards here but have not been able to get my configuration to work correctly, anyone please help.

I have a domain name [www.oncreationcomplete.com](www.oncreationcomplete.com) which i have registered with Network Solutions and have set up and registered the name server ns1.oncreationcomplete.com and ns2.oncreationcomplete.com which both use the IP 216.254.79.186

If i browse to [http://216.254.79.186/](http://216.254.79.186/) everything works fine, but when i browse to [http://oncreationcomplete.com](http://oncreationcomplete.com) it doesnt work.

I want the ubuntu box to host DNS, I dont want to use forwarding or dyndns or some sort of third party solution. I want this box to host the mx, cname, a records and for all purposes host the DNS itself.

If anyone could point me in the a direction which would show me how to set up the name server onthis box so thee FQD will resolve here.

thanks in advance
- Ken

---

### Post by clyrrad on 2007-06-05
Out of curiosity how long ago did you register the domain name?

It can take 24-48 hours for your domain name to propagate across the Internet.  If it's not been that long since you registered your domain, give it a bit more time see if the propagation has not taken place yet.

Cheers!

---

