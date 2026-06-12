---
title: "ddclient"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Apache0c on 2009-05-05
I've been searching for an answer on this but I cant seem to find a comprehensive ddclient tutorial. They all appear to assume some level of basic knowledge that I must not have.

I started to install ddclient manually, I set up the conf file and the cache directory. But then I couldnt find a tutorial that explained the pid file for the startup script so I went to the package manager and installed ddclient from there. That created the startup script and I also went back after that and checked my conf file and it was still there and so was my cache dir. I just cant help thinking I missed something though.

I used one of the provided conf files on the dyndns website. But it doesnt seem to be working. I tested it by going in to my account on dyndns and changing the ip address for my webserver. Then I restarted my computer. I have the ddclient.conf file set for daemon=60. So I waited a while but it never updated. Is there something I left out?

This is my conf file:

> # Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=60
cache=/var/cache/ddclient/ddclient.cache
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=<my username here>
password=<my password here>
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
<my.domain.here>
custom=yes, example.comFor the cache file, I just made a file and named it ddclient.cache. Is there anything else I need to do for that? Also, can I just delete the last line of the conf file since I'm only worried about the one domain right now?

I'm running mint 5 LTS (hardy)

Thanks for all your help guys!

---

### Post by cybergalvez on 2009-05-05
ddclient only updates your ip when your ip changes and is different from its cache.  so you will have to force a change or delete you cache file

---

### Post by Apache0c on 2009-05-05
Awesome. Ok, that is good info, thanks! 

So what about the cache file I made, is that all there is to it?

---

### Post by cybergalvez on 2009-05-05
I would delete the cache file you made and let ddclient create it

---

### Post by Apache0c on 2009-05-05
ok, thanks!

---

