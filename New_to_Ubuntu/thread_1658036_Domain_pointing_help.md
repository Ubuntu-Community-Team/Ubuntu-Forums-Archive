---
title: "Domain pointing help"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by emumu on 2011-01-02
Hi all, I am new to the server stuff and I just signed up for a VPS service for a WordPress. I have finally set up everything I need for my site to display the blog page, that's say DoONE.com. Now, I have another domain name, DoTWO.com, that I'd like to pointing to the same blog site. Same document root. 
 
I went to my domain registrar of DoTWO.com and changed the nameservers to ns1.DoONE.com and ns2.DoONE.com. What else do I need to do from my server end to make this happen? 
 
I think I am missing something so when I enter DoTWO.com into the browser, it resolved with a "You don't have permission to access / on this server.
Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request." message.
 
Also, another stupid question, I have my DoONE.com working in the browser, but when I type in [www.DoONE.com]("http://www.DoONE.com"), it resolved to the Google search page. Where do I have to configure so both URL (with www AND without www) would point to my blog site?
 
Thanks for any insights!!! :confused:

---

### Post by Funkey Monkey on 2011-01-02
This is not the correct forum to solve your query.

Ask Google.

---

### Post by fabricator4 on 2011-01-02
> **emumu said:**
> 
Also, another stupid question, I have my DoONE.com working in the browser, but when I type in [www.DoONE.com]("http://www.DoONE.com"), it resolved to the Google search page. Where do I have to configure so both URL (with www AND without www) would point to my blog site?

Thanks for any insights!!! :confused:

This is probably (certainly) the wrong forum for you questions, but...

It takes some time for the data to propagate around the domain name servers, so allow 24 hours and try again.  In my part of the world this process can be measured in days rather than hours, so YMMV.

Is there some reason you went with a VPS service rather than just a hosting service?  With a hosting service all of this would have been the issue of the service provider.

Chris.

---

### Post by emumu on 2011-01-02
> **fabricator4 said:**
> This is probably (certainly) the wrong forum for you questions, but...
 
It takes some time for the data to propagate around the domain name servers, so allow 24 hours and try again. In my part of the world this process can be measured in days rather than hours, so YMMV.
 
Is there some reason you went with a VPS service rather than just a hosting service? With a hosting service all of this would have been the issue of the service provider.
 
Chris.
 
Thanks for the response! Certainly appreciate it. I guess I'll wait a bit. It's just very different from when I was on the shared host plan where two domains pointing to same site happened almost instantaneously. I just need to change the NS info from the registrar side and change the domain pointing on the hosting c-panel and it would take effect right away.
 
Now with the VPS, all you get is the Ubuntu installed. By installing the LAMP, I managed to get the WordPress to work for one domain, but not the second one. 
 
The price of managed VPS is getting quite reasonable these days. I could use this opportunity to pick up some latest Ubuntu knowledge. Also, my shared hosting service is getting very slow for unknown reasons. Now, I have installed the wordPress on the VPS, it's much faster on both the response time and the loading time.
 
Cheers,
 
ET

---

### Post by Ravenshade on 2011-01-02
Don't you normally have to wait 24 hours for the systems to catch up?

---

### Post by emumu on 2011-01-02
> **Ravenshade said:**
> Don't you normally have to wait 24 hours for the systems to catch up?
 
 
Possible, but so far, the domain pointing was very fast if I used the c-panel from the shard hosting service. When I set up my first domain today, pointing to my server (register NS and pointing to NS were all done in minutes).
 
But, for the www vs. non-www, this is my first time encountering the problem. I don't know where can I make both to work. :confused:
 
Thanks.
 
ET

---

### Post by fabricator4 on 2011-01-02
> **emumu said:**
> Possible, but so far, the domain pointing was very fast if I used the c-panel from the shard hosting service. When I set up my first domain today, pointing to my server (register NS and pointing to NS were all done in minutes).
 


Ah, it's a case of not all things being equal.  If your ISP is using the same DNS as your hosting service the update appears to be instantaneous.  People using other ISP's and more distant DNS's may be hours or even days behind.

Send me your URL if you like and I'll try it, but I'm betting that I can't access it for _days_
fabricator4 at yahoo dot com

Chris

---

