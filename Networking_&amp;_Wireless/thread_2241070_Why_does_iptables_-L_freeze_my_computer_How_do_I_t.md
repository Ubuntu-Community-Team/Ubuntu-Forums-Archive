---
title: "Why does iptables -L freeze my computer? How do I troubleshoot this?"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by free_wary on 2014-08-24
I am setting up some iptables rules to control internet traffic on my desktop ubuntu installation. In the past (using ubuntu 12) I used iptables with no problem. It was pretty easy to list out the tables and edit them.

Now I'm using a fresh installition of Trusty (v14 LTS). Running any iptables command in terminal freezes my entire computer and I have to reset. 

I've searched many forums and didn't find any similar complaints.

Does anyone know what is causing this? Can anyone give me some tips how to troubleshoot this?

---

### Post by Doug S on 2014-08-24
Hi, and welcome to Ubuntu forums.
> **free_wary said:**
> Does anyone know what is causing this?No. This is a strange one.> **free_wary said:**
> Can anyone give me some tips how to troubleshoot this?The first thing I would try is to eliminate lookups from the list command. I would use this:```
sudo iptables -n -L
```or this```
sudo iptables -v -x -n -L
```instead of this```
sudo iptables -L
```.

---

