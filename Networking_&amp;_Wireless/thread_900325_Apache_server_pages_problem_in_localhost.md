---
title: "Apache server pages problem in localhost"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2008-08-25
I'm trying to get this thing working from another app's mini-server - the app contain a very stripped-down html server, and can be pointed towards a port - nothing more. Usually, its use is very simple: point your broswer to [http://localhost:port/](http://localhost:port/) and you get the page.

However, when I run this mini-server, I also have (I believe by default) Apache2 running as a service in my Ubuntu. Which means, as soon as I go into [http://localhost/](http://localhost/), it gives me "**IT WORKS!!**".

I tried pointing my mini-server towards port 50000, but again, I can't see a thing; it's as though Apache knows it's not the one serving that page, so it doesn't allow any other server to output its pages. 

Any thoughts on how to fix this?

Please remember: at all times, I cannot use any other address than "http://localhost:specificport/", as this is for a very specific use.

---

### Post by SpaceTeddy on 2008-08-25
if you want apache to listen on a different port you need to edit the ports.conf in the /etc/apache2 directory and add the port there. 
As for the redirecting - take out this line from the default in /etc/apache2/sites-available
>  RedirectMatch ^/$ /apache2-default/
which is redirecting you to the "it works" page.

hope it helps :)

---

