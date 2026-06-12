---
title: "WiFi Connecting"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by AlaMal on 2009-03-26
How do I set up a wireless link with my existing Windows set up. I don't have a taskbar to access it.

---

### Post by billgoldberg on 2009-03-26
> **AlaMal said:**
> How do I set up a wireless link with my existing Windows set up. I don't have a taskbar to access it.

I don't know what you mean with "taskbar".

I presume you want to be able to share files between Ubuntu and Windows (aka set up a home network)?

I've written an easy to follow guide on this, read it here:

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

---

### Post by Kevbert on 2009-03-26
Welcome to Ubuntu.
Assuming you are running Ubuntu. If you go to System-Administration-Restricted Drivers you may be able to install a driver from there if you have a wired internet connection.
If not, we need to know what wireless adapter you are using. Select Applications-Accessories-Terminal and enter
```
lspci
```
Post back the line which says Network Controller with the information displayed. For example, Broadcom BCM4306 Rev01.

---

