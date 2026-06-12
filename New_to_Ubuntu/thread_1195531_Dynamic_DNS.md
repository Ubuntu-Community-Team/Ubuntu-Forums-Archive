---
title: "Dynamic DNS"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by t0pcat on 2009-06-23
Very noob with Ubuntu/Linux. I have Ubuntu 9.04,Jaunty Jackalope installed and working great. I have a dynamic IP and I am trying to host a web site using a dynamic DNS service. I have Apache installed and can see 127.0.0.7 loopback page. Can anyone tell me how to configure apache to resolve to the IP address with the host name the dynamic DNS service gives me? Or point me in the right direction.....I appreciate any help.

---

### Post by magh-87 on 2009-06-23
> **t0pcat said:**
> Very noob with Ubuntu/Linux. I have Ubuntu 9.04,Jaunty Jackalope installed and working great. I have a dynamic IP and I am trying to host a web site using a dynamic DNS service. I have Apache installed and can see 127.0.0.7 loopback page. Can anyone tell me how to configure apache to resolve to the IP address with the host name the dynamic DNS service gives me? Or point me in the right direction.....I appreciate any help.

I have not tried this out myself so I cannot speak with any experience since I the opportunity for me to do hosting of my own has not come up yet, however [URL="http://www.opendns.com/"]opendns[/UL] was suggested to me by a friend of mine. There are plenty of free alternatives out there, try Google and see what your results are like.

Best of luck.

[Edit] I forgot to ask, are you using the server edition or desktop? Let me know how it works out for you either way. I'm still debating which route I want to take when I start doing some website hosting for my friends.

---

### Post by jimv on 2009-06-23
You need to tell the DNS service what your IP address is so it knows where to point people.  Here's a good read:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Once you have your Dynamic DNS configured correctly, you need to setup your router to forward port 80 to your computer.  This means that the router will know that your computer is supposed to handle all HTTP requests.  If you need assistance with that, do a Google search for your router model and the words "port fowarding".

---

### Post by t0pcat on 2009-06-24
> **jimv said:**
> You need to tell the DNS service what your IP address is so it knows where to point people.  Here's a good read:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Once you have your Dynamic DNS configured correctly, you need to setup your router to forward port 80 to your computer.  This means that the router will know that your computer is supposed to handle all HTTP requests.  If you need assistance with that, do a Google search for your router model and the words "port fowarding".


Thanks guys I will keep you posted.

---

