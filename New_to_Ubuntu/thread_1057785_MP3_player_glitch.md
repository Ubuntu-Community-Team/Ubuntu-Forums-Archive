---
title: "MP3 player glitch"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by priyanka on 2009-02-02
Hi, Just installed Ubuntu 8.04 and it has been working great! However I just realised that I cannot play mp3 files on it.
I have a default rhythmbox player and when I try to play mp3 it shows import error 'gstreamer plugins to decode mp3 files cannot be found'

I then downloaded Exaile thinking that might help but havent been able to install it.

I havent been able to install audacity to onvert it to ogg file either.

Is there anyway to correct the gstreamer problem??

---

### Post by Eisenwinter on 2009-02-02
You need to get the correct gstreamer codecs.

I'm not sure as for the package names, but you can open up a terminal, and type **sudo apt-cache search gstreamer***, and then install the ones you need.

---

### Post by tarps87 on 2009-02-02
You can get them from the restricted package:
```
sudo apt-get install ubuntu-restricted-extras
```
This will install the mp3 codecs, some others and java
ubuntu-restricted-extras

---

### Post by erblro on 2009-02-02
I am brandnew, and fighting with the same problem:
>>sudo apt-get install ubuntu-restricted-extras<< doesn't work.
Shows me: try >> apt-get update << doesn't work
or >> --fix-missing<< unknow operation.

Any new Idea ??

---

### Post by tarps87 on 2009-02-02
> **erblro said:**
> I am brandnew, and fighting with the same problem:
>>sudo apt-get install ubuntu-restricted-extras<< doesn't work.
Shows me: try >> apt-get update << doesn't work
or >> --fix-missing<< unknow operation.

Any new Idea ??

Try:
```
apt-get update --fix-missing
```
or
```
apt-get update -f
```

Do you have an internet connection?

---

### Post by leonardo_neo on 2009-02-02
> **priyanka said:**
> Hi, Just installed Ubuntu 8.04 and it has been working great! However I just realised that I cannot play mp3 files on it.
I have a default rhythmbox player and when I try to play mp3 it shows import error 'gstreamer plugins to decode mp3 files cannot be found'

I then downloaded Exaile thinking that might help but havent been able to install it.

I havent been able to install audacity to onvert it to ogg file either.

Is there anyway to correct the gstreamer problem??

You need codecs to play all these media file formats, which are not given with the Ubuntu OS by default because of some legal issues.

First install the restricted extras package.

Open main menu---> Accessories---> Terminal 

Then copy paste this command

> sudo apt-get install ubuntu-restricted-extras

Enter, it will ask for root password, type that and then enter. It will install some packages. You are almost done for most of the codecs.

For some more media files, you would like to install 'Medibuntu' repository and codecs. Just open the link given below and it will guide you how you can add the repository.

> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once the repository is added, then you need to install these packages

**libdvdcss2**
**w32codecs**

How to install these packages, is guided in the link given above itself.

Hope this helps your problem :)

---

### Post by halovivek on 2009-02-02
> **priyanka said:**
> 

Is there anyway to correct the gstreamer problem??

Welcome to forums Priyanka
[Here]("https://help.ubuntu.com/community/RestrictedFormats") you can find the full details how to install the extras for ubuntu.

---

