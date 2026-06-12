---
title: "Need something that does ProxyAuthentication for me"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by mikuskuikku on 2007-07-09
Hi!
At this network I have a squid proxy that doesn't let anybody out on the internet without authenticating him self.
I got username and password for this, and when I start my Firefox i get a question (popup) to enter my username and pw (everything works just fine).
But the proxy keeps on forgetting me, so I need to retype this every 15minutes. 
Some functions cant authenticate (like aptitude) so I have hard time updating my system (have a workaround by changing all 'http' to 'ftp' in sources.list).
So I need something that does the authentication for me.

The proxy is a Squid (Digest Authentication).
I can't change anything in the proxy (I don't have access).
For the moment I don't know any more than that about the proxy (but if you have suggestions, I can try to figure out some more info).

Any suggestions?

---

### Post by mikuskuikku on 2007-07-10
I forgot to say that nothing helps that I tested so far...

(myname, mypass, and proxyip is hidden in these ouputs)

--------------------------------------------------------------------------------
My current settings looks like this:
```
mh@inspiron:~$ cat /etc/apt/apt.conf
Acquire::http::Proxy "http://myname:mypass@proxyip:8080/";
```

```
mh@inspiron:~$ export | grep http
declare -x http_proxy="http://myname:mypass@proxyip:8080"
```

--------------------------------------------------------------------------------
And when I test ... I get the result ...
```
mh@inspiron:~$ sudo apt-get update
Ign http://wine.budgetdedicated.com feisty/main Packages
Ign http://wine.budgetdedicated.com feisty/main Sources                  
Err http://wine.budgetdedicated.com feisty/main Packages                 
  407 Proxy Authentication Required
Err http://wine.budgetdedicated.com feisty/main Sources
  407 Proxy Authentication Required
```

```
mh@inspiron:~$ wget http://www.google.com
--11:06:14--  http://www.google.com/
           => `index.html.4'
Connecting to 192.168.82.129:8080... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
11:06:14 ERROR 407: Proxy Authentication Required.
```

Is there anything else I can do?

---

