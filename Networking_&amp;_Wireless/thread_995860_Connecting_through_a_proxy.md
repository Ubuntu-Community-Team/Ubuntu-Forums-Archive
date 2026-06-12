---
title: "Connecting through a proxy"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by namd3r on 2008-11-28
I cannot get to my gnome desktop anymore, but I know it can be solved by a quick update to my computer from a terminal.  Problem is, my internet access goes through a local proxy, so anytime I do an update without first logging in through my browser, it fails because all the packages are hit with 302 redirects.

Is there any way of logging into the proxy through a terminal or editing a file to do it for me so that I can update?

---

### Post by Nostalos on 2008-11-28
Quick and Easy Oneshot way (aka not set permanently)

> 
export http_proxy="http://username:password@myproxy.domain.com:8080



Assuming your proxy is on port 8080 of course.  Then just execute you apt-get normally 

> sudo apt-get upgrade  

or whatever your preferred command line method.

---

### Post by namd3r on 2008-11-28
When logged in, this is the website that I get redirected to.  Will that be what I enter for the proxy?

```
https://192.168.0.1:442/modules/auth/cgi-bin/ssllogin/login.cgi
```

---

