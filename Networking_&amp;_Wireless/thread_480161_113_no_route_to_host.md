---
title: "113 no route to host"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by SkyRaider on 2007-06-21
Dear ubuntuforums,

Since this morning I´m still getting this annoying error (could not connect to myip, 113 no route to host) So we thought lets go to the school above us and let us check there because our schoolproxy blocks everything. We are connected to their network and we can do everything but if we want to download updates and programs through the add/remove application it says Could not connect to myip, 113 No route to host, while we arent even on our schoolnetwork downstairs
Does anybody have a clue what the problem is?.

Kind regards,
Roland

---

### Post by spd106 on 2007-06-22
This usually indicates that you have no internet gateway or that the default route is set to the wrong address. Try looking at the routing table, it should look something like this. Where the gateway is at 192.168.0.1
```
:~$ ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.5 
default via 192.168.0.1 dev eth0 

```

Try to ping an external server such as google.com, if it resolves an address then you know DNS is working. But if it fails with no route to host then you have a gateway issue.
```
ping google.com
```

Also try using wget to grab a webpage such as [www.google.com](www.google.com).
```
wget http://www.google.com
```
 If it fails with no route to host then you probably have a web proxy problem.

---

### Post by andersdd on 2007-10-30
Hi,

I am having problems accessing external sites.  My Gutsy server can resolve URLs to the correct IP but when I tried a wget as you suggested it failed with no route to host.  

Can you please explain further your meaning about a web proxy problem.

Thanks.




Also try using wget to grab a webpage such as [www.google.com](www.google.com).
Code:

wget [http://www.google.com](http://www.google.com)

If it fails with no route to host then you probably have a web proxy problem.

---

### Post by spd106 on 2007-10-30
What I meant was that either requests to the web proxy were going unanswered or the web proxy itself is having trouble dealing with the request. Both of these would be a separate issue to the DNS problem or routing problems.

If it's a web proxy problem then it's probably a good idea to contact the administrator.

---

