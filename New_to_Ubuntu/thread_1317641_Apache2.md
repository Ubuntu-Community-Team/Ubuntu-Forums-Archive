---
title: "Apache2"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by bediff on 2009-11-06
Here is my problem: I have a domain and I want to host it from home with Apache2, but I really don't know how. Searched a lot on the internet and haven't found a basic example of how to host a simple html file and I hoped you could help me. 

I have Apache2 installed and I'm running Ubuntu 9.10.

Thx in advance,
Bediff

---

### Post by wojox on 2009-11-06
What happens when you load:

```
http://localhost/
```

---

### Post by bediff on 2009-11-06
It says:

It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.


This means it works only on my home network, right?

---

### Post by 3rdalbum on 2009-11-06
> **bediff said:**
> It says:

It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.


This means it works only on my home network, right?

Yep. But all you need to do is put your files into /var/www and tell your router that any incoming requests on port 80 should be forwarded to your computer. Then give people your IP address ([www.whatismyip.com](www.whatismyip.com)) and they can see your site.

---

### Post by bediff on 2009-11-06
That's great information! Thank you very much :)

But if I have a domain ( e.g. [www.ioi.ro](www.ioi.ro) ) how can I use that instead of my ip?

---

