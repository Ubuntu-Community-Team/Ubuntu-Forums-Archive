---
title: "Firefox Google issue"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by mh91 on 2010-09-06
Alright this is my first time ever trying a linux os so I chose ubuntu. I'm using 10.04 and have been trying to get google.com to load up for a while now and nothing works. I changed my home page to [www.google.com]("http://www.google.com") and at first it was redirecting me to something called conical that looked like a store and now it just loads up a blank white page. Google search also doesn't work and yahoo search sends me to yahoo autos search. I have no idea what is going on, I would just like the browser to work the way it does in windows.

---

### Post by DemonBob on 2010-09-06
First, what is the hardware specs of your machine? 

Are you trying to connect over wireless? or over a hard wire? 

If wireless, have you tried a hard wire?

---

### Post by mh91 on 2010-09-06
Wired, I'm posting on the ubuntu machine, everything else is working fine on the browser except yahoo and google

---

### Post by DemonBob on 2010-09-06
post your /etc/resolve.conf, /etc/hosts, and /etc/network/interfaces


```
sudo gedit /etc/resolve.con
sudo gedit /etc/hosts
sudo gedit /etc/network/interfaces
```

Sounds like a DNS issue.

---

