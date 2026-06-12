---
title: "HTTPS port open..!!.."
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Noob2011 on 2011-03-29
Hello, 

Absolute noob here... I just checked my netbook security at SheildsUP ([www.GRC,com]("http://www.GRC,com")) and i got this warning. (pls. see picture attachment).  Should i need to be worried?. How do i fix it, if this is a problem... 

Thanks for your time

D

Dell Inspiron Mini 
2GB RAM, 250 HDD
Ubuntu 10.04 (Lucid)

---

### Post by Grenage on 2011-03-29
Urgh, GRC.

Do you per chance have a home router/gateway?  Does it have remote administration enabled?

---

### Post by Noob2011 on 2011-03-29
Hello Grenage, 

Yes, i do connect via ADSL broadband modem . I logged into the modem and checked . Please see picture. It does not seem to be open... 

thanks for your help. 

regards

---

### Post by Grenage on 2011-03-29
I suppose a program could be using uPnP to forward a port, what does this show:

```
netstat -lnptu
```

Anything on 443?

---

### Post by Noob2011 on 2011-03-29
I don't see it. I have attached screenshot.. 

thanks

---

### Post by Grenage on 2011-03-29
Alas, I am at a loss.  Either the modem/router is actually listening on HTTPS, the port scan is wrong, or netstat isn't showing what's listening.

Have you run a second scan, for comparison?

---

### Post by Noob2011 on 2011-03-29
Hello Grenage... its gone mate... i just checked again and it was fine.. thanks so much for asking me to check again....  dont know why i got a false warning before though.... :confused:        any ideas??... i use " gnome-gmail-notifier 0.10.1 "  thats constantly on.... . does that create this problem... ?? ..

Thanks for everything .. cheers...

---

### Post by Grenage on 2011-03-29
It's possible that the notifier uses HTTPS and the scan coincided with a check, but I'm glad to hear that it's not persistent!

---

### Post by Noob2011 on 2011-03-29
Cool... thank you so much mate... All the best....

---

