---
title: "configure apache to allow just one IP able to access"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by byenary on 2009-03-06
Hello

Since i use a port forward in a router and i can't refuse sources on that level, i want to leave it to apache to refuse everybody unless the lanip range 192.168.123.0 and 1 Wan ip, i assume i'll have to do this with htaccess but do not have a clue how...


Thx all

---

### Post by Joeb454 on 2009-03-06
If you don't want people to be able to access your webpage from outside your network, you can just disable that specific port forward on your router...

---

### Post by ibuclaw on 2009-03-06
I don't think this can't be done with apache.

But as well as just disabling port forward on your router (as local connections don't need to be port forwarded), if you are adamant to leave it open, you also have Linux iptables (Linux's builtin firewall) that you can setup to only allow incoming connections on that port to be only from local addresses.

The only problem with that is that iptables takes quite a learning curve to learn how to use it efficiently.
Fortunately, there is an excellent guide here: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Regards
Iain

---

### Post by kanikilu on 2009-03-06
I'm pretty sure you should be able to do this in your apache conf file:

```
<Directory /var/www>
 Order deny,allow
 Deny from all
 Allow from [WAN IP]
 Allow from 192.168.123
</Directory>
```

Obviously change the path to the appropriate path you want to protect, and change the wan IP.

---

### Post by byenary on 2009-03-06
Hello,

I need to let in just 1 IP from outside (a fellow company) wich can make use of the intranet.
Was just having a look in the config trough webmin and the option is present in webmin but prefer the manual way of course...

---

### Post by byenary on 2009-03-06
Thx kanikilu that is it and it works!

---

### Post by kanikilu on 2009-03-06
> **byenary said:**
> Thx kanikilu that is it and it works!

No problem. I use this same approach to limit access to phpmyadmin on my servers to only a particular subnet on my network...

---

### Post by byenary on 2009-03-06
Why bother doing that?
phpmyadmin authenticates using the mysql passwords wich are not known by the users...

---

### Post by OffAxis on 2009-03-06
> Why bother doing that?
He probably does it to further limit access. A password is portable, modifiable, and steal-able. A specific machine or group of machines adds another layer of security.

---

### Post by kanikilu on 2009-03-06
Just an added layer of security...paranoia, maybe ;-) My approach is to deny everything and then start re-adding only what is necessary.

---

### Post by sp0nge on 2009-03-06
It may be easier to set access controls like this through the firewall, IMO.

---

### Post by kanikilu on 2009-03-06
> **sp0nge said:**
> It may be easier to set access controls like this through the firewall, IMO. I do use a firewall to restrict access to certain ports, but just out of curiosity, how would you control access to a specific web directory with a firewall alone?

---

### Post by Kareeser on 2009-03-06
You can't, and that's the disadvantage of sp0nge's suggestion.

The best and most efficient way was altering the sites-available config, which you did.

---

### Post by byenary on 2009-03-06
My cheapass dualwanlinksys router does not have the right features to accomplish that...so i'm doomed to do it like this, but I trust apache.
Although i will have a look to buy a juniper or something like that...

---

