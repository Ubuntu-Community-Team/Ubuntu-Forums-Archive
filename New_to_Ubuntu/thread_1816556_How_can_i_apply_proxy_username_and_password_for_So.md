---
title: "How can i apply proxy username and password for Software centre..?"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by aruntu on 2011-08-02
I have connected Firefox with my Wifi at my college but i am unable to connect the Ubuntu software center to the Internet because i don't know how to apply the proxy user-name and password to it.. I have **checked out the network proxy** thing but it does not help..

Using Ubuntu 11.04

---

### Post by srisharan on 2011-08-02
To enable internet through proxy in Ubuntu change proxy settings in network proxy(search in dash in 11.04 ).Then click on the details button to input username and password.You can also enable the apt to use proxy.Open apt.conf file 
```
gksudo gedit /etc/apt/apt.conf
```

and the type your proxy settings in the following way

```

Acquire::http::proxy "http://user:pass@proxy:port/";
Acquire::ftp::proxy "ftp://user:pass@proxy:port/";
Acquire::https::proxy "https://user:pass@proxy:port/";
```

---

### Post by aruntu on 2011-08-02
> **srisharan said:**
> To enable internet through proxy in Ubuntu change proxy settings in network proxy(search in dash in 11.04 ).Then click on the details button to input username and password.You can also enable the apt to use proxy.Open apt.conf file 
```
gksudo gedit /etc/apt/apt.conf
```and the type your proxy settings in the following way

```

Acquire::http::proxy "http://user:pass@proxy:port/";
Acquire::ftp::proxy "ftp://user:pass@proxy:port/";
Acquire::https::proxy "https://user:pass@proxy:port/";
```

I Already have this proxy code but should i replace or append the above code..
```
Acquire::http::proxy "http://172.16.16.2:3128/";
Acquire::ftp::proxy "ftp://172.16.16.2:3128/";
Acquire::https::proxy "https://172.16.16.2:3128/";
```

---

### Post by srisharan on 2011-08-02
> **aruntu said:**
> I Already have this proxy code but should i replace or append the above code..
```
Acquire::http::proxy "http://172.16.16.2:3128/";
Acquire::ftp::proxy "ftp://172.16.16.2:3128/";
Acquire::https::proxy "https://172.16.16.2:3128/";
```

Ok then change the code to this.

```
Acquire::http::proxy "http://user:pass@172.16.16.2:3128/";

```

where user is your actual username and pass is you actual password

---

### Post by KHALED-LELA on 2011-11-08
if i have password ended with @ ???????????

---

