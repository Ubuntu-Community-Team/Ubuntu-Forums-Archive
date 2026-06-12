---
title: "How to install additional software without internet"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by borneux on 2009-03-13
I have downloaded the ubuntu repository DVD and have successfully installed ubuntu on my gf's computer. She doesn't have an internet connection and everytime I'm trying to install additional software, synaptic always try to update the repo list. How do I resolve this and install programs only from the DVD repo? Thx in advance

---

### Post by martrn on 2009-03-13
> **borneux said:**
> I have downloaded the ubuntu repository DVD and have successfully installed ubuntu on my gf's computer.

There are GB's in the reposotories, and I think they could fit onto more than 7 DVD's (excluding alternative repositories). 

> **borneux said:**
> She doesn't have an internet connection and everytime I'm trying to install additional software, synaptic always try to update the repo list. How do I resolve this and install programs only from the DVD repo? Thx in advance

edit your /etc/apt/sources.list by
```
sudo nano /etc/apt/sources.list   ## or
sudo gedit /etc/apt/sources.list
```
and comment out everything with a ## before everything begging with http:// or ftp://   !!
You can also do this from the gnome system menu as well by un-cheking a few boxes which does the same thing.  Check your /etc/apt/sources.list after just to make sure.  Make sure the dvd's are in the /etc/apt/sources.list in the correct fashion or you have set up a local repository.

sudo nano /etc/apt/sources.list

---

### Post by freak42 on 2009-03-13
not sure if it helps, but try playing with the settings in

System->Administration-> Synaptic Package Manager->Settings->Repositories->Ubuntu Software

maybe this page helps as well (adding cd-roms as repos is handled here)
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories)

hth

---

