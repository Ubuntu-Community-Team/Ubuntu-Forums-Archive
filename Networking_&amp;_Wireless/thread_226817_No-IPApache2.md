---
title: "No-IP/Apache2"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Dylan103 on 2006-07-31
Can somebody give me a detailed tut on howot set these up?
Im running on a Linksys WRT54G router, with the ports 80 open(i beleive, i went to port forwarding and went 80 to 80 and enabled, so theirs open). But Ineed to know how to get it set up.

---

### Post by az on 2006-07-31
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by Dylan103 on 2006-07-31
Doesnt work, but [http://localhost.com](http://localhost.com) works, my port 80 is open.
[http://dylanhost.no-ip.org](http://dylanhost.no-ip.org)
I setup and configures the no-ip and ran it, and is running. I dont see it working.

---

### Post by az on 2006-07-31
Your router is the dynamic dns client, not your box.

---

### Post by Dylan103 on 2006-07-31
Well at my router config, i goto enable DDNS and i see two options, DYNDNS.com and TZO.com

---

### Post by Dylan103 on 2006-07-31
BUMP!
Anybody?

---

### Post by Dylan103 on 2006-08-01
Please anybody? I need this ASAP, canyouseeme.org can see me.
Do i need to sudo apt-get install no-ip ?
or run apache2 some how?

---

### Post by adamkane on 2006-08-01
```

sudo apt-get install apache2

```

Reboot.

---

### Post by az on 2006-08-01
> **Dylan103 said:**
> Well at my router config, i goto enable DDNS and i see two options, DYNDNS.com and TZO.com

So use one of them.  It's up to your router to do that, not the boxes on your internal network to be the client.

---

### Post by Dylan103 on 2006-08-01
Well it used to work until I upgraded to 6.06.

---

### Post by adamkane on 2006-08-02
There's your problem. :)

Re-install. :(

---

### Post by cantormath on 2006-08-02
> **Dylan103 said:**
> Doesnt work, but [http://localhost.com](http://localhost.com) works, my port 80 is open.
[http://dylanhost.no-ip.org](http://dylanhost.no-ip.org)
I setup and configures the no-ip and ran it, and is running. I dont see it working.


your ISP, ie) cox or charter, blocks port 80 so that you do not do that.
use https.

[a great tutorial]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

---

### Post by cantormath on 2006-08-02
oh, and try using a free dns system, 
afraid.org
signup, its free, point your domain to their name server, and then set up you dns on that site to point at your machine.  They also have some cool scripts to sync your ip, that you do have to pay for, or use the half *** no ip version.

some routers support a dynamic ip syncing fuction, but they generally only support certain sites, check out your router to see if you can do that.
ie)dyndns, dns made easy.

---

### Post by cantormath on 2006-08-02
On a different note, does anyone know how to delete a duplicate post?

---

### Post by adamkane on 2006-08-02
Find and harangue a forum administrator.

---

### Post by az on 2006-08-02
> **adamkane said:**
> There's your problem. :)

Re-install. :(

That's rarely the case.

---

