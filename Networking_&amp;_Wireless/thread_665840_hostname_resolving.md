---
title: "hostname resolving"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Pitxyoki on 2008-01-12
This must be a very dumb question but I have already searched for a while and can't find a good answer.

Until some time ago, when I typed
```
http://C-2:5432
```
I could access my other computer's web interface using a browser. Lately, I haven't been able to do so and Firefox ends up telling me:
> Unable to connect
Firefox can't establish a connection to the server at [www.c-2.com:5432](www.c-2.com:5432).

On the Windows boxes on the network, typing C-2:4532 on Firefox's address bar is working as it should... On the other hand, if I use the other computer's IP address instead of it's hostname, it goes fine on Debian and Windows.

Also, I'm getting this (which I'm not sure in what way it can be good or bad):
```
$ nmblookup C-2
querying C-2 on 192.168.2.255
192.168.2.177 C-2<00>
```

I believe this might be related to samba or something... But I really don't know... Maybe I should read some manuals, but I really don't have the time for that now.
Any help would be appreciated.

PS- Please don't tell me to edit the /etc/hosts file, because my network's IPs change from time to time and I had this working before without having touched that.

---

