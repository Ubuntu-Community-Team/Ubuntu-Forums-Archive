---
title: "wget works after two shots"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by SIGTERMer on 2008-11-24
hi,
I am writing a program that obtains an ip from a router, i am using wget to get it. the data on the router can only be accessed via username and password (HTTP).

here is my problem... the first time it requests the page, it gets a "401 unauthorized Authorization failed", but the second time it secedes with a weird message complaining that it cant WRITE to status.html???

this is how i'm using it:
[B]wget -t 7 -w 5 --waitretry=14 -O - --http-user=USER --http-password=PASSWORD [http://192.168.1.1/Status.htm](http://192.168.1.1/Status.htm)
[/B]

can anyone tell me whats going on?

thanks

---

