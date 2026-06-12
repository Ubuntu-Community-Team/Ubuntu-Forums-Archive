---
title: "specific DNS configuration"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by cnschulz on 2007-08-21
Gday

I hope my question is specific enough... 

I have an ubuntu server on my home network on 192.168.1.3 called "zoidberg". It is visible on the internet as xxxx.homeip.net. All good.

Now that I am using Apache and SVN from my laptop, id rather have one name to reference this server regardless of whether i am on the local net or the internet.

Could someone point me in the right direction on how to configure BIND so that my laptor will point to the right host when xxxx.homeip.net is referenced from the local network?

*any* help appreciated

Cheers.

---

### Post by will71110 on 2007-08-21
several ways to do it but the easiest would be to mod your host file.  Go into network setings, click on the tab that says hosts then click add and add the ip and the name you want it to point to.  Or you can click on the DNS tab and add homeip.net in the search domain.

---

### Post by cnschulz on 2007-08-21
thanks, 

however i would rather not have to edit the laptops hosts file evertime i come or go from the network.

homeip.net is one of those dyndns sites so i dont own the domain either... id just like the local DNS to resolve xxxx.homeip.net to 192.168.1.3. other than that, i have no requirement for a local dns.

i just have no idea if this is possible or how to do it!?

:)

---

