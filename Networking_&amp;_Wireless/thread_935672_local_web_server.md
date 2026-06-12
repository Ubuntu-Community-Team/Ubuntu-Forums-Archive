---
title: "local web server"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by benen on 2008-10-01
Hey everyone,
I'm a web developer that has recently moved to ubuntu. I found it easy to set up a web server on my ubuntu box but am unable to access it from my laptop through my wireless network. My ubuntu box is named benen-linux and from my laptop I was temporarily able to visit [http://benen-linux](http://benen-linux) and view my web folder but now that is unavailable. It also doesnt work on the host machine either. This is from a fresh install, my previous install worked just fine but i'm not sure how i set it up. I can visit it just fine using the hosts ip though, so there is no connection problem

Thanks
Benen

---

### Post by cariboo on 2008-10-02
You can just edit your /etc/hosts file to alias the computer name to an ip address:

```
192.168.1.100    benen-linux 
```

Of course substitute your web servers ip address for the one above.

Jim

---

