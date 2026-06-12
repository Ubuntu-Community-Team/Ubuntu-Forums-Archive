---
title: "Configure Proxy with Empathy"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Raouf on 2009-12-13
How to Configure Proxy with the new IM "Empathy" in Ubuntu 9.10
thanks

---

### Post by keplerspeed on 2009-12-13
I would assume that all you need to do is set the system proxy: system>preferences>Network proxy.

---

### Post by Raouf on 2009-12-13
I already configured Network Proxy and for example Update Manager is working properly

---

### Post by keplerspeed on 2009-12-13
Looks like a [bug]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/304889"), currently triaged. You may have to revert to pidgin for the time being.

---

### Post by t0mc4t on 2010-02-08
Have the same issue here...
How to set proxy on empathy?
Thanks..

---

### Post by daspooky on 2010-02-10
I managed to use empathy through our work's proxy by 

1. installing tsocks: sudo apt-get install tsocks
2. configuring the file /etc/tsocks.conf (add the proxy server)
3. launching empathy this way: tsocks dbus-launch empathy

have fun!

---

### Post by chitresh4u on 2010-02-17
> **daspooky said:**
> I managed to use empathy through our work's proxy by 

1. installing tsocks: sudo apt-get install tsocks
2. configuring the file /etc/tsocks.conf (add the proxy server)
3. launching empathy this way: tsocks dbus-launch empathy

have fun!

Can you please post your /etc/tsocks.conf.

---

### Post by nbulchandani on 2010-03-05
Hello,
Could someone explain how to use empathy behind a http proxy..may b via proxy chains
Thanks

---

### Post by Lowzow on 2010-03-08
Hey!
as nbulchandani,

I wonder how to set up empathy with an automatic proxy. (the who need an URL)

The problem is that this proxy needs authentication. Where to set username and password?

As it is I only get firefox to work under my schools proxy. (and spotify under wine for some reason.)

---

### Post by nbulchandani on 2010-03-10
Hey,
i was asking can someone tell me how to use empathy behind proxy server via proxychains...

---

### Post by lophie on 2010-03-31
> **nbulchandani said:**
> Hey,
i was asking can someone tell me how to use empathy behind proxy server via proxychains...

Pretty much just like tsocks (Mentioned above) and config file is /etc/proxychains.conf and it's straight forward with examples.

---

### Post by rengolin on 2011-08-15
> **Raouf said:**
> How to Configure Proxy with the new IM "Empathy" in Ubuntu 9.10
thanks

If you have access to squid, add the following rules to your ACL


acl SSL_ports port 5050     # Yahoo! Msn
acl SSL_ports port 5222     # Google Talk

That will allow tunneling back and forth and allow empathy (and pidgin) to connect via proxy.

---

