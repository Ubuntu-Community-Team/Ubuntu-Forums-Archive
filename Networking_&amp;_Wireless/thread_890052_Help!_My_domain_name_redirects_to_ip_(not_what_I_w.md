---
title: "Help! My domain name redirects to ip (not what I want)"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2008-08-14
I'm new to network configuration, so I'm not sure how to make my domain work the way I want it to. I'm thinking it might be a problem with my dsl modem/router/web server setup.

Does anyone know what I need to do in order to make my domain stay the same - rather than converting to my ip (in the web browser URL bar) once the page is loaded?

Thanks!

---

### Post by tamoneya on 2008-08-14
isnt that what happens by definition with domain names.  The idea is that you translate them to IPs so that the computer can find the servers they correspond to.

---

### Post by jonathanmotes on 2008-08-14
> **tamoneya said:**
> isnt that what happens by definition with domain names.  The idea is that you translate them to IPs so that the computer can find the servers they correspond to.

OK, maybe I should have chosen a better title. Yes, that is what domains do, but usually you still see your domain in the URL bar after typing it in. In my case, the URL location in Firefox shows the ip address that my domain points to after I enter my domain.....

In other words, when I type in [http://google.com](http://google.com) I always see "http://google.com" in the address bar - the ULR in the address bar doesn't change to "64.233.167.99." Do you see what I mean?

---

### Post by tamoneya on 2008-08-14
> **jonathanmotes said:**
> OK, maybe I should have chosen a better title. Yes, that is what domains do, but usually you still see your domain in the URL bar after typing it in. In my case, the URL location in Firefox shows the ip address that my domain points to after I enter my domain.....

In other words, when I type in [http://google.com](http://google.com) I always see "http://google.com" in the address bar - the ULR in the address bar doesn't change to "64.233.167.99." Do you see what I mean?

Okay now I get it.  Does this happen in all web browsers or just firefox.  I want to try and figure out if it is firefox we should be looking into or if we need to look into some of your computers config files.

---

### Post by bab1 on 2008-08-14
Are you running Apache?  I think it is in your webserver config files.

---

### Post by jonathanmotes on 2008-08-14
> **tamoneya said:**
> Okay now I get it.  Does this happen in all web browsers or just firefox.  I want to try and figure out if it is firefox we should be looking into or if we need to look into some of your computers config files.

I'm not real sure.....
I will probably have to wait until tomorrow to tell because my ip address changed, and the domain will have to be reconfigured (I don't own the domain - so I will have to get the owner to reconfigure it for me.)

I know that the same problem exists for other people (not on my network) though. My brother tried it from across town (Probably using Firefox on Windows Vista) with the same results.

Thanks for the help!

---

### Post by jonathanmotes on 2008-08-14
> **bab1 said:**
> Are you running Apache?  I think it is in your webserver config files.
Yes, I am running Apache.

Also, I am going to try to set up a dynDNS account so that I can continue testing until the domain is back up.

---

### Post by jonathanmotes on 2008-08-14
OK, I just got my [http://dyndns.com](http://dyndns.com) account set up and it works fine.....
This is really strange....
The domain that I was using was from [http://www.domainsarefree.com/](http://www.domainsarefree.com/). Has anybody used them?

---

