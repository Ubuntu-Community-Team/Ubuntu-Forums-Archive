---
title: "Internet slow!!"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-01-18
I installed ubuntu 9.04 along with windows vista (dual boot).
The problem is , I am experiencing slower browsing and downloading rates with the same connection settings compared to what I am getting on Windows vista.
What can the problem possibly be ?

---

### Post by Silent Warrior on 2010-01-18
Quite likely the Linux-drivers for your networking hardware aren't as neat and shiny as their official Windows-counterparts. It seems few hardware manufacturers release drivers for Linux (never mind their quality...), but without knowing what card you're using, it's impossible to conjure up a reason or fix for this.
It would help with some output of lspci, but I don't do that often enough to confidently tell you what options you should use. Just search for 'lspci' on these forums, and you should get a number of suggestions.

---

### Post by chuina on 2010-01-18
> "What can the problem possibly be ?" 

Problem can be using internet by a proxy connection.
I some threads,some proxy connection won't allow to install soft from Ubuntu soft sources.

---

### Post by Linuxforall on 2010-01-18
Linux network drivers are far superior, in the average I experience far superior speeds with no long term slow downs, however in your case it looks like the dreaded ipv6 issue, also try change your dns server to either google's, open dns or dnsadvantage.

For turning off system wide ipv6, take a look here at  [http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

---

### Post by wojox on 2010-01-18
For Jaunty you want to disable IPv6 with:

```
gksudo gedit /boot/grub/menu.lst
```

and add this after your uuid

```
ro quiet splash ipv6.disable=1
```

And reboot.

Here's how to change DNS Servers as well:

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

---

### Post by ThePinkWitch on 2010-01-18
> **Linuxforall said:**
> Linux network drivers are far superior, in the average I experience far superior speeds with no long term slow downs, however in your case it looks like the dreaded ipv6 issue, also try change your dns server to either google's, open dns or dnsadvantage.

For turning off system wide ipv6, take a look here at  [http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

Hey Thanks for this info..my internet is heaps faster since I tried that. :D

---

### Post by peace.gangsta on 2010-01-18
> **chuina said:**
> Problem can be using internet by a proxy connection.
I some threads,some proxy connection won't allow to install soft from Ubuntu soft sources.

Thanks a lot for support guys :D 
I also face problems when trying to downloading from repositories especially while upgrading :( .. things always go wrong :'( . Any help there..

---

