---
title: "Problems with squidGuard set up"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by aberry5555 on 2008-04-24
Hi there everyone. Ok, so here's my set up so far: I have set up a working squid proxy server with a few regex acls, it all seems to work fine and, with the short blacklist that we've made ourselves, it does file type and site blocking perfectly fine.

The problem I'm having, though, is that I have installed squidguard so that I can add shalla's list on top of our current configuration so as to save us some work. 

I followed the following set of instructions (and I followed them to a T, I'm pretty sure, though I could be wrong) but I can't for the life of me get squid to start once I put the redirector line in to squid.conf:

[https://help.ubuntulinux.org/community/SquidGuard](https://help.ubuntulinux.org/community/SquidGuard)

After following the troubleshooting section I think I've found the reason why squid won't start, but can't get any further when I issue the following command:

```
sudo echo "http://porn.com 10.0.0.1/ - - GET" | squidGuard -d -c /etc/squid/squidGuard.conf 
```

I get the following error message:

```
loading dbfile /var/lib/squidguard/db/porn/domains.db 
Error db_open: Permission denied
```
(please excuse the reference to porn, I'm using a blacklist of one site to test)

Now I'm pretty sure I've set all the necessary permissions, I followed all of the possible permission commands in the help document, all of the necessary folders are user: proxy group: proxy and all permissions are set in the described way. Maybe it has something to do with this document being slightly dated, and a different user is now required? or perhaps I'm missing some simple step but whatever I do I can't get around this permission denied error. 

If anyone can help and needs me to show any logs and the like please let me know as this is starting to get very frustrating, heh.

Thanks in advance,

Alex

---

### Post by aberry5555 on 2008-04-25
Bump.

---

### Post by whitegourd on 2008-08-07
Due to the permissions error, I'd say that you'd probably have to modify all the blacklists permissions and restart squid to see if that resolves your issue.

```

chmod -R 770 /var/lib/squidguard/db/*
chown -R proxy.proxy /var/lib/squidguard/db/*
/etc/init.d/squid restart

```

---

