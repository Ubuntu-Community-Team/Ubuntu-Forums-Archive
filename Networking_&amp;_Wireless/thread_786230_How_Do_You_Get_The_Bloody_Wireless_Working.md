---
title: "How Do You Get The Bloody Wireless Working????"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by jamieh on 2008-05-07
Whenever I successfully get WiFi working, it just goes away when I restart the computer!

I followed multiple tutorials on how to get my TEW-423PI wireless card working, and they all work until I restart. And I am NOT using a live-cd!

Can someone post a tutorial that has worked for them?

Thank you SO MUCH if you can! :)

EDIT: I have ubuntu 8.04
Sorry if I sound mad.

---

### Post by Ayuthia on 2008-05-08
It sounds like you need to have a module added to /etc/modules or else you need something blacklisted in /etc/modprobe.d/blacklist.  Can you provide us a link to one of the tutorials you used?  It will help us see what might be missing.

---

### Post by jamieh on 2008-05-08
> **Ayuthia said:**
> Can you provide us a link to one of the tutorials you used?  It will help us see what might be missing.

[http://ubuntuforums.org/showthread.php?t=400258](http://ubuntuforums.org/showthread.php?t=400258)

Thanks!

---

### Post by Ayuthia on 2008-05-08
If doing the following makes it work:
```
sudo modprobe ndiswrapper
```
Make sure that ndiswrapper is in /etc/modules:
```
cat /etc/modules|grep ndiswrapper
```
If it is not there:
```
echo ndiswrapper|sudo tee -a /etc/modules
```
will add it for you.

Hope that helps!

EDIT:
If that doesn't work, please post the following:
```
ndiswrapper -v
ndiswrapper -l
lshw -C network
```

---

