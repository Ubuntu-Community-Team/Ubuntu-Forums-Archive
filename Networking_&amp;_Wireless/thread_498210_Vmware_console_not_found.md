---
title: "Vmware console not found"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by gheywood on 2007-07-11
Hello,

I have VMWare Server installed on Ubuntu server 7.04.

It looks like something has fallen over since the management console is no longer available. When I connect to the box on [http://server/8222](http://server/8222) or [http://server/8333](http://server/8333) I get a "page cannot be found" error. Connecting via the VMWare Server Console (the actaul app) works fine.

On Win2003, I would probably restart the IIS service as a start, but not sure how to do the equivalent on a linux server. I guess it is apache that hosts the management console? 

How can I restart apache without bouncing the box?

Any other suggestions on the likely problem?

Cheers

---

### Post by scxtt on 2007-07-11
it should be [http://server:8222](http://server:8222) or [http://server:8333](http://server:8333) assuming those #s are supposed to be ports ... i'm also not sure if you're *forced* to use SSL, making it http**s**:// ...

bouncing apache(2) = sudo /etc/init.d/apache2 restart

---

### Post by gheywood on 2007-07-11
Thanks, yeah I was using a colon not a / when trying it, just not when posting it :)

Will try and restart apache and see how it goes.

Cheers

---

