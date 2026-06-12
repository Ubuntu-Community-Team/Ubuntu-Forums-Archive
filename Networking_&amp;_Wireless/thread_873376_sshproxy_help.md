---
title: "ssh/proxy help"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by boblemur on 2008-07-28
hi all,

what im trying to achieve is: my uni has access to these online library resorces, however im unable to get to them at home because of my ip not belonging to the uni... so what i want to do is basicly use my uni as a proxy....(sounds easy right)

I HAVE:

 -my computer (124.171.x.x)
 -full administrative rights to my computer and my router
 -uni server  (x.x.edu.au)
 -ssh access on uni server
 -proxy auth rights on uni proxy (x.cs.x.edu.au)

I DO NOT HAVE:

  -sudo access on uni server(obviously)
  -access to any uni side settings...

a map of the computers involved....(rarther unsure of the uni side):


```
my pc:  =====|                                                          |===|uni server(with ssh access)
             | = |netgear router|== internet... == |uni webserver(proxy)|
lanpc's: ====|                                                          |===|other uni computers
```


now tcp/ip flow needs to be:

 mypc > router > internet > uni webserver > uni ssh server > uni webserver > [www.google.com](www.google.com)

---

### Post by dmizer on 2008-07-29
Take a look at this post: [http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

And, here: [http://www.linux.com/articles/56945](http://www.linux.com/articles/56945)

---

### Post by boblemur on 2008-07-29
i have tried proxychains, with no luck however i doubt i set it up correctly, but i was looking for a solution without using anything except fire fox and built in ssh tools of ubuntu...

so i can easily port it to my windows computer....

---

### Post by dmizer on 2008-07-29
Step 1: install and configure ssh with [cygwin](http://www.cygwin.com/) on your windows machine ([putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/) can also be made to work).
Step 2: ssh to your server with the following command:
```
ssh -D 9999 username@x.x.edu.au
```
Step 3: configure firefox for a SOCKS proxy where
host = localhost
port = 9999

You're proxying through your university's server.  There is no need to configure anything at your home location.

These directions are outlined in more detail in the links I gave above.

---

