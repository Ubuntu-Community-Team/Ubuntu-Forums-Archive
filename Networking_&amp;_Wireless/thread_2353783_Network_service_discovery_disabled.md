---
title: "Network service discovery disabled"
date: 2017-02-24
forum: Networking &amp; Wireless
---

### Post by anon24 on 2017-02-24
I keep getting this error when I boot Ubuntu 16.04:

"Network service discovery disabled
Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled."

I'm fairly new to the Ubuntu world. Can someone explain this to me?

---

### Post by wildmanne39 on 2017-02-24
I use to get that message along time ago and it can be safely ignored but if you want to fix it have a look at the following link.
[https://ubuntuforums.org/showthread.php?t=1632952](https://ubuntuforums.org/showthread.php?t=1632952)

---

### Post by wildmanne39 on 2017-02-24
*Thread moved to **Networking & Wireless**.*

---

### Post by Morbius1 on 2017-02-25
And once again it all depends on your definition of "fix".

[1] If you don't use it then by all means disable it.

[2] If however your local network depends on for printers discovery and / or file sharing then my suggestion is as follows:

The issue here is how or if your ISP is using .local domains internally - which is something they should not do. To see if that is the case run this command:
```
host -t SOA local
```
It should come back with something like this:
> Host local not found: 3(NXDOMAIN)                      
If instead it comes back with this then your ISP is drunk and disorderly:
> local has SOA record localhost. xxxx.yyyy.zzz.                      
One way out of this is to change the DNS servers you use from the one supplied by your ISP to say ... google ( 8.8.8.8 ).
As a check on this run the host command again using Google's DNS:
> morbius@mw1865:~$ host -t SOA local 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

Host local not found: 3(NXDOMAIN) 


---

### Post by macstl on 2017-02-25
I added line= dns-nameservers 8.8.8.8 8.8.4.4 to my interfaces file and got rid of that error message on both 16.04 and 14.04 computers

---

