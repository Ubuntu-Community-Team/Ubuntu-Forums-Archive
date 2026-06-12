---
title: "Connecting Delay"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by Riskbling on 2007-10-13
Here is a screenshot if this helps; [http://img164.imageshack.us/img164/9651/screenshotmf8.png](http://img164.imageshack.us/img164/9651/screenshotmf8.png)

I am very unfamiliar with linux. Everytime I try to go back to the network options it is always set to LO(I set to etho)  I dont know if that has anything to do with it. The internet works it's just that it takes exactly 15 seconds for it to connect to the site (tried on multiple sites, get 15 seconds everytime) Then once it has connected to the site everything loads fast like it would normally. When I was at my school we had to connect through a proxy (192.168.1.1:8080) to access the internet. I am not sure if that would automatically change any of my settings. I took all the proxy settings out now that im at home and dont use it.

---

### Post by j.bunce on 2007-10-13
Configure it with network manager, not network tools.

---

### Post by Riskbling on 2007-12-05
Alright, I am almost determined it has something to do with my network now. Here I am a month later installing it on my laptop after giving up on my older machine. I have the same exact problem as I did before I have no idea why?

It takes approx. 10-15 seconds to connect to the website and once it connects to it. The web page loads just like it normally would. 

Is there any type of router settings that would do this?

---

### Post by timcredible on 2007-12-05
maybe remove ipv6 dns lookups in firefox.  enter about:config in the url line, search for ipv6, change the default setting

---

### Post by Riskbling on 2007-12-08
Wow. Thanks. This worked. Thank you very much.

---

