---
title: "fixing network address on linksys router"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by daviescr on 2008-01-26
I have a linksys WRT54G router that assigns my network addresses and then I have a Ubuntu server for storage and website development. I have recently started playing with wordpress sites and whenever I loose power I get stuck. It seems that wordpress uses the IP address to define the site name.
The Question:
So other than going through the wordpress setup again, is there a way for me to set a fixed IP address in the router or server at boot up? 
Possibly somebody else has used this type of "dynamic wordpress" setup before and knows how to change the wordpress config to use the server name instead of the ipaddress..

I have no desktop GUI on my server box so answers need to be at the command line level.

thanks in advance,


-------------------------------
windows free lifestyle

---

### Post by Mikecore on 2008-01-28
look up the command "ifconfig"


or in a terminal do 

```

man ifconfig

```

---

