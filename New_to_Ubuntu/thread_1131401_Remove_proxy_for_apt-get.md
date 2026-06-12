---
title: "Remove proxy for apt-get"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by boblemur on 2009-04-20
Hey all,

im trying to run:

```
sudo aptitude update
```

however, i get the responce of:

```
Err http://mirror.ucc.usyd.edu.au intrepid Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

```

im using a different mirror (but i know it works iv been using it for a while)

I get this response especially the "Could not connect to localhost:8080" because i usually use a ssh tunnel as a proxy.


I HAVE TRIED:
- adding the following to my /etc/environment file:
```
http_proxy=""
ftp_proxy=""
https_proxy=""

```

here is the output of:

```
nick@nick-laptop:~$ env | grep proxy
nick@nick-laptop:~$ sudo env | grep proxy
nick@nick-laptop:~$ 

```
please help, anything information is much appreciated.

---

### Post by spiderbatdad on 2009-04-20
can you disable this under System Preferences >> Network Proxy?

---

### Post by Slim Odds on 2009-04-20
apt-get uses its own config files to define a proxy.

/etc/apt/apt.conf.d/01proxy

---

### Post by boblemur on 2009-04-20
Slimodds: that file dosent exist on my system. which is weird, because your not the first person to mention it.

spider: thanks, you were close.

even though the proxy wasnt enabled, apt-get was still using the "manual" proxy settings because it didnt check to see if the proxy was set to none or manual. so i will report the bug.

---

### Post by spiderbatdad on 2009-04-20
wonder if localhost was listed under the ignore hosts tab.

---

### Post by mavsky on 2009-11-07
By clicking reset and choosing manual in  System Preferences >> Network Proxy and tehn restarting my laptop works on my end. 

Thanks spiderbatdad.

---

### Post by Rack1600 on 2011-01-04
I found that my proxy settings were stored in /ect/apt/apt.conf file, in the form:
Acquire::http::Proxy "http://myproxy:8080/"

I found it by grep'ing for my proxy name in the etc/apt folder.

I had nothing in my proxy settings for Auto or Manual, and I had already tried setting them in command line with http_proxy="" etc.

Hope this helps someone.

---

