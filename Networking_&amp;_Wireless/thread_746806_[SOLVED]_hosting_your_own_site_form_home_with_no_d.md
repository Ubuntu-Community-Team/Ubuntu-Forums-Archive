---
title: "[SOLVED] hosting your own site form home with no domain"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by gnulogic on 2008-04-05
does anyone know how to host your own site form home using your ip address instead of a domain name, or any other way to host a site from home with out using a domain name?

---

### Post by superprash2003 on 2008-04-05
you first need to install apache for that [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5)

if you dont have a static ip, then you could have problems accessing your pc from the internet as your ip will keep changing.

---

### Post by kutjara on 2008-04-05
> **gnulogic said:**
> does anyone know how to host your own site form home using your ip address instead of a domain name, or any other way to host a site from home with out using a domain name?

In addition to setting up a webserver like Apache, you'll need to use a DNS redirection service like the one offered by [www.dyndns.com](www.dyndns.com). They'll give you a static IP address that maps to your home account's IP address, so users will always be able to reach your website using the same IP address.

---

### Post by gnulogic on 2008-04-06
I already have a static ip address.  so how do people reach my computer just type in my ip address in the address bar?  I don't want to pay for a domain or get one. I just want to set up a website from home using my ip i know people do it, i just dont know how.  I have apache, I just dont know how to set my website using my static ip.

---

### Post by superprash2003 on 2008-04-06
have you opened port 80 on your router/modem?

---

### Post by Eiríkr on 2008-04-06
Provided that you've set up Apache and opened port 80 in your firewall, and forwarded port 80 from your router to your server, then yes, folks would just type in your static IP address to access your site. 

HTH,

Eiríkr

---

### Post by gnulogic on 2008-04-06
yea port 80 is forwarded to the computer hosting the site.  I just dont know how to get to the site am I supposed to put the ip address in the address bar of a browser to get there?

---

### Post by Eiríkr on 2008-04-06
Yes, that's what you'd do.  The browser address bar can be used for either fully qualified domain names, like "www.google.com", or for IP addresses, like "74.125.19.147" (also for Google).  Try this IP address for yourself to see.  

Cheers,

Eiríkr

---

### Post by gnulogic on 2008-04-06
thank you everyone for your help you helped me solve my problems, I really appreciate it.  I am very happy now.

---

### Post by Eiríkr on 2008-04-06
Always be sure to try to access your site from a computer that is definitely not on your network.  Although you may type in the external IP, security for the firewall and other options can work out differently when the computer you're browsing from is part of your internal network, so while you can access that external IP from an internal computer, you migth discover that accessing from an external computer doesn't work (depending on your setup) -- so be sure to test.  ;)

Cheers,

Eiríkr

---

### Post by gnulogic on 2008-04-06
thanks I'll check from an outside location.  I am happy i have gotten this far.

---

### Post by twright on 2008-04-06
if the server is accessible over the internet be sure to secure it:
[http://www.google.com/search?q=ubuntu+server+security&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=ubuntu+server+security&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

also it might be a good idea to get a free domain and set that to redirect to you server because a domain is a lot easier to remember than an ip address

---

### Post by gnulogic on 2008-04-06
where and how would i get a free doimain name?

---

### Post by superprash2003 on 2008-04-06
[www.no-ip.com](www.no-ip.com) offers a free service called "no ip free" where you will get a domain like myname.servehttp.com or myname.no-ip.org .. you have some choices like that..its totally free..

---

### Post by gnulogic on 2008-04-06
thanks, I now have a free domain, free hosting via apache and my computer, I now have more freedom and control over how and what i want to do with my site.  thanks again for everyones support.

---

### Post by gnulogic on 2008-04-06
does anyone know a good what you see is what you get html editor that is comparable to kompozer?

---

### Post by Eiríkr on 2008-04-08
I'm not familiar with kompozer, but other wysiwyg editors I'm aware of that are also in the repositories include amaya and iceape (i.e. mozilla).

---

