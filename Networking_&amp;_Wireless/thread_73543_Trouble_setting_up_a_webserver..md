---
title: "Trouble setting up a webserver."
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by amdserver on 2005-10-09
Im a newbie to linux (Days old), but I love it.

I've been thinking about building a web server out of my old computer for quite some time. So I download Ubuntu Hoary 5.04, installed it on a clean HDD, made 3 partitions /boot, / , and swap. Installation went great, better than expected. I've updated all the packages. Downloaded Webmin, web server and control panel, the server works locally. Since I’m behind a router, I forwarded the necessary ports to the server's local IP. I've got a free DNS, [http://amdserver.kicks-ass.net](http://amdserver.kicks-ass.net), so now am at a loss as to where the problem may be. Could anyone recommend a free web control panel? I think it may be Webmin.

---

### Post by nemin on 2005-10-09
> **amdserver]Im a newbie to linux (Days old), but I love it.

I've been thinking about building a web server out of my old computer for quite some time. So I download Ubuntu Hoary 5.04, installed it on a clean HDD, made 3 partitions /boot, / , and swap. Installation went great, better than expected. I've updated all the packages. Downloaded Webmin, web server and control panel, the server works locally. Since I’m behind a router, I forwarded the necessary ports to the server's local IP. I've got a free DNS, [http://amdserver.kicks-ass.net](http://amdserver.kicks-ass.net), so now am at a loss as to where the problem may be. [/QUOTE]Well, what exactly **is** the problem now? The serer is fully functional in the local network? But it doesn't work from the internet, or what's the point?
Sorry if I missed something  said:**
> 
Could anyone recommend a free web control panel? I think it may be Webmin. Webmin is great for beginners indeed. Though, be **very sure** you're using an incredibly difficult password and you always have the latest version, to minimize the security risk...

---

### Post by amdserver on 2005-10-09
I want my server to be accessable from the outside (Internet).

---

### Post by nemin on 2005-10-10
[QUOTE=amdserver]I want my server to be accessable from the outside (Internet).[/QUOTE]
The server should be accessable from the internet if it works locally and if ports are forwarded correctly. Are you sure your routers forwards ports correctly? Maybe you could put the router in DMZ?

---

