---
title: "phpb3 and a new router"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by zachery on 2011-03-17
So i changed from a linksys router to a tenda router today and everything is fine people tell me they can see my website and my forums but i can not see my forums on my machine when i go to 

[http://zacherytest.dyndns.info/phpBB3](http://zacherytest.dyndns.info/phpBB3) it doesnt load for me but my friend said it loads for him any ideas?


thanks

---

### Post by user1397 on 2011-03-17
it's not loading for me.  maybe some parts of my guide in my signature can help a bit in your situation, the one about setting up a web server

---

### Post by zachery on 2011-03-17
> **ubuntuman001 said:**
> it's not loading for me.  maybe some parts of my guide in my signature can help a bit in your situation, the one about setting up a web server


i looked it over i dont think the answer to my issue is there because as i said it was working fine before i switched routers

---

### Post by zachery on 2011-03-17
someone please lmk if you can see my main website page

[http://zacherytest.dyndns.info/](http://zacherytest.dyndns.info/)

---

### Post by dryicebomb on 2011-03-17
are you sure that you have forwarded port 80 through the router to the webserver?

---

### Post by zachery on 2011-03-17
> **dryicebomb said:**
> are you sure that you have forwarded port 80 through the router to the webserver?


NO.             Start Port-End Port             To IP Address             Protocol             Enable               Delete                      
1.-192.168.0.  TCP  UDP  Both 


i have it 80-80 and it is enabeled and set to 100

its a w268r tenda

---

### Post by dryicebomb on 2011-03-17
Sounds fine, assuming that the ip address of your webserver is set to 192.168.0.100 and that the webserver is listening for requests on that address. Also do you have any sort of firewall running on your server like iptables?

---

### Post by CharlesA on 2011-03-17
I could see the test page. :) However, I can't get to the forums for some reason.

---

