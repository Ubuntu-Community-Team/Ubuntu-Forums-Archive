---
title: "Could not resolve 'in.archive.ubuntu.com'"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by adit on 2009-08-29
I am not able to use apt-get.  I get the following error.
```
~$ sudo apt-get update
Err http://in.archive.ubuntu.com jaunty Release.gpg                         
  Could not resolve 'in.archive.ubuntu.com'
```
But I am able to browse the internet using konqueror.

---

### Post by NoaHall on 2009-08-29
Is it working with Synaptic? If not, go to software sources (or run gksudo gedit /etc/apt/source.list) and disable that line. And have you installed the key for it? You must download and install a key before using any custom sources.

---

### Post by halitech on 2009-08-29
the base address loads up for me in a browser, are you sure you have the information correct in your apt/sources.list file?

could you post your sources list so we can take a look at it?

---

### Post by adit on 2009-08-29
I have attached the full output of 'sudo apt-get update' and my /etc/apt/sources.list
I think the problem is with resolving ip address of 'in.archive.ubuntu.com'.  But I am able to browse internet with the same computer.  I am using Kubuntu 9.04

---

### Post by NoaHall on 2009-08-29
Hm.. Looks like something's going very wrong. is this a fresh install? And you say you can browse? Have you tried using aptitude or synaptic?

---

### Post by halitech on 2009-08-29
if you open a web browser, can you load
```
http://in.archive.ubuntu.com
```

---

### Post by sandyd on 2009-08-29
seems like a DNS error to me
have you tried OpenDNS?

---

### Post by adit on 2009-08-29
This is a fresh install.  This is Kubuntu 9.04.  So there is no synaptic package manager installed by default.  I tried aptitude also.  I got the same error messages inside aptitude window.

---

### Post by adit on 2009-08-29
I am able to load "in.archive.ubuntu.com" in Konqueror.

---

### Post by NoaHall on 2009-08-29
oh, right, didn't know you were using KDE. 

I'd try installing gnome or xfce, see if you get the same problems - kde has always been troublesome for me.

---

### Post by halitech on 2009-08-29
Look for Adept and see if that is installed (it should be the default package manager for Kubuntu)

Since you can load in.archive.ubuntu.com in a browser, that eliminates it being a DNS issue and I would think its something to do with the format of how you have it entered.Try disabling that one by putting a # in front of it and enable the others by removing the #


deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

---

