---
title: "The ISA Server requires authorization to fulfill the request."
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by aliahmadi1367 on 2015-02-02
Hi,
I installed Ubuntu 14.10.
My network requires proxy and authentication to connect to the internet.
I edited the file /etc/apt/apt.conf to this value

```
Acquire::http::proxy "http://domain\username:password@myproxyserverip:8080";
Acquire::ftp::proxy "http://domain\username:password@myproxyserverip:8080";
Acquire::https::proxy "http://domain\username:password@myproxyserverip:8080";

```
also edited /etc/bash.bashrsc
```
export http_proxy=http://domain\username:password@myproxyserverip:8080/
export ftp_proxy=http://domain\username:password@myproxyserverip:8080/
```

but i couldn't connect to internet via Firefox to surf or terminal to update my repositories and install softwares.

what should i do?
what is missing here?

---

