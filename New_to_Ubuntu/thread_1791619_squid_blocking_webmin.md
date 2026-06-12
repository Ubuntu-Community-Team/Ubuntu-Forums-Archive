---
title: "squid blocking webmin"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2011-06-27
So I have squid up and running and its working a treat, only problem is I cannot get access to webmin at [https://192.168.1.100:10000](https://192.168.1.100:10000)

part of squid.conf file below.
```

acl localnet src 10.0.0.0/8 
acl localnet src 172.16.0.0/12 
acl localnet src 192.168.0.0/16 
acl SSL_ports port 443
acl webmin url_regex "/etc/squid/webmin.acl"
acl webmin_port port 10000
http_access allow CONNECT webmin_port localnet
http_access allow CONNECT webmin_port localhost

```

Contents of webmin.acl are as followed

```

https://192.168.1.100:10000

```

Here is the error from cache.log

```

 The request CONNECT 192.168.1.100:10000 is DENIED, because it matched 'SSL_ports'
2011/06/27 19:33:41| The reply for CONNECT 192.168.1.100:10000 is ALLOWED, because it matched 'SSL_ports'
2011/06/27 19:33:41| The request CONNECT 192.168.1.100:10000 is DENIED, because it matched 'SSL_ports'
2011/06/27 19:33:41| The reply for CONNECT 192.168.1.100:10000 is ALLOWED, because it matched 'SSL_ports'

```

The only reference I can find to the SSL_ports in squid.conf are

```

#Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
http_access deny manager
# Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge
# Deny requests to unknown ports
# http_access deny !Safe_ports # EDITED HERE
# Deny CONNECT to other than SSL ports
http_access allow CONNECT !SSL_ports

```

I know it is just a simple setting, I just can't figure out which?

Anyone shine some light

---

### Post by robsoles on 2011-06-28
I haven't used squid but I thought I would have a poke around for you and I think I've spotted the odd 'bit and piece' that might help you.

Please review: [http://www.linuxquestions.org/questions/linux-server-73/https-doest-work-through-squid-770374/](http://www.linuxquestions.org/questions/linux-server-73/https-doest-work-through-squid-770374/)

I get the impression that you need to define 10000 as a 'safe port' (using the syntax/method they are using at above link) and then you need to repair the squid.conf file to look more like EricTRA is trying to get the OP to do in post #4 at that other forum.

I may be mistaken, it may be that just changing your line:```
http_access allow CONNECT !SSL_ports
```to```
http_access allow CONNECT SSL_ports
```might just make it go but you should reinstate the line that reads```
http_access deny !Safe_ports
```as the last line in squid.conf if I have understood what I've been looking at in the last five minutes.

At least I have bumped your thread: If you try anything based on the advice at the other forum and it doesn't give you joy then post your attempt & results please - if nobody romps in with better help I will lift my game and try harder for you ;)

---

