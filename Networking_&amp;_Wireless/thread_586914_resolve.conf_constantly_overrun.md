---
title: "resolve.conf constantly overrun"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by noamh on 2007-10-22
Hi,

my /etcresolve.conf is constantly overrun by some process.
I have followed the directions in 

[http://ubuntuforums.org/showthread.php?t=7280]("http://ubuntuforums.org/showthread.php?t=7280")

And it partialy solved the problem. Meanig that if I do ifup and then ifdown, rsolve.conf
return to it's desired value:

```
search lan
nameserver 194.90.1.5
nameserver 10.0.0.138
```


However after some time, something is overruning it with some default value:

```
search lan
nameserver 10.0.0.138
```


Any ideas ?

---

### Post by noob12 on 2007-10-22
Yes.  Are you using DHCP on any interface?  If so, you need to use either the **prepend domain-name-servers** or **supersede domain-name-servers** directives in **/etc/dhcp3/dhclient.conf** if you want to specify your own name servers. For more info see **man dhclient.conf** and you can see examples in the first section of this thread here on a related but different topic: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

