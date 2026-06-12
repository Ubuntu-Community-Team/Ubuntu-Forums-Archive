---
title: "Kismet - suid priv dropping disabled"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by zdzis&#322;aw on 2006-12-30
I have problem with Kismet. I set up the configuration file with the suiduser name... but it always says
```
 suid priv-dropping disabled and not secure when starting up.
```
I've search kismet forum and I've found that:
> 
You have to recompile to get that functionality if it was turned off in the build. In other words, uninstall the deb and build it from source.

Theres 3 ways to install kismet:

1. No suid abilities. Everything runs as root. This means you trust me not to have made a stupid bug in the code anywhere thats somehow exploitable. I'm pretty good about that, but...
2. Suid-drop without suidroot. This is probably the best for most packages. This means kismet drops privs to the specified user after spawning the channel control proc, but you have to start it as root. (ie, sudo kismet)
3. Suid-drop with suidroot. This means any user can start kismet and bork the network connection. Good for laptops, bad for anything else. 


How I can recompile kismet using suid-drop without suidroot?

---

### Post by tturrisi on 2006-12-30
Not sure, but you should still be able to run kismet from a root term as any user.  Applications > Accessories > Terminal (as root)

---

### Post by zdzis&#322;aw on 2006-12-30
> **tturrisi said:**
> Not sure, but you should still be able to run kismet from a root term as any user.  Applications > Accessories > Terminal (as root)

I've tried from root terminal, but I still have:
```
Suid priv-dropping disabled.  This may not be secure.[\code]

I've changed kismet.conf:
[code]
# User to setid to (should be your normal user)
suiduser=zdzislaw

```

but I still ahve error msg: Suid priv-dropping disabled.  This may not be secure. 

How I can recompile this package with  suid priv-dropping enabled?

---

### Post by tturrisi on 2006-12-30
[http://svn.kismetwireless.net/code/trunk/README](http://svn.kismetwireless.net/code/trunk/README)

---

