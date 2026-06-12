---
title: "Cannot Connect to my Ubuntu Server using domain name"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by DJSBX on 2008-11-08
Alright, so let me show you my network setup before I explain the question.

Cable Moden(WAN) --> Router
Router1 --> Computer 1
Router2 --> Ubuntu Server
Router3 --> Computer 2

Now lets say my ISP gives my IP address as (1.1.1.1),  so that would go to my router.

Computer 1 is (2.2.2.1)
Server is (2.2.2.2)
Computer 2 is (2.2.2.3)

Now I have my ubuntu server set up with virtual hosts. 

[www.djsbx.com](www.djsbx.com) and [www.lainternationalautosales.com](www.lainternationalautosales.com) 

(Yes, my router has port 80 forwareded to the appropriate machine)

Now Any of you should be able to get to those 2 web sites using the domain names I specified above, but my computer (computer 1) and my fathers computer (computer 2) can not get there. 

Now, I think the problem is that Im inside my router and when I go to either of those 2 url's it resolves to my routers ip and some complications arise there (thats my theory).

If I access my server via the internal address (2.2.2.2) I can access the default web site (which is the lainternationalautosales one), thus I cannot access the djsbx one because the server serves either web site depending on the url it was accessed by.

Please let me know if you guys know any way that I could access my 2 sites on my server using the url addresses, if there is a way I can get it to resolve to internal ip's or something.

Thanks

---

### Post by widor on 2008-11-08
Have you tried adding lines like the following to the /etc/hosts file on computers 1 and 2?

2.2.2.2 [www.djsbx.com](www.djsbx.com)
2.2.2.2 [www.lainternationalautosales.com](www.lainternationalautosales.com)

---

### Post by DJSBX on 2008-11-08
Oh sorry, computers 1 and 2 are windows machines.

---

### Post by widor on 2008-11-08
That's okay. You can still add those lines to the hosts file. It's just in a different location on a Windows computer (and depends on which version of Windows you're using). See this [_link_]("http://en.wikipedia.org/wiki/Hosts_file#Location_and_default_content") for details.

---

### Post by DJSBX on 2008-11-10
Ahh yes, that is exactly what I needed. Thank you :D

---

