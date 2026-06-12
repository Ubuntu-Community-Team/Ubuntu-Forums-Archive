---
title: "Confused: Guayadeque SVN is what?"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by DayLite on 2010-10-01
I don't understand what SVN means :confused:
I installed version 0.2.7-1227
Then I added the PPA so I can get all the updates.

I noticed that in the Ubuntu Software Center it tells me Guayadeque is not installed. The version in the Software Center is version: 1262~lucid-1 (guayadeque-svn)

What is the svn stand for? I want to use a stable version. What do I put in the Software sources that will update the stable version when a new one is released. I think I have the wrong one:confused:

This is what I copied to the Software Sources: > deb [http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu](http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu) lucid main 

---

### Post by Hippytaff on 2010-10-01
SVN - [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

---

### Post by Hippytaff on 2010-10-01
From what I've read you can get the stable version from the ubuntu repository - 
 
```

sudo apt-get install **guayadeque**

```
 
then it's the standard
```

sudo apt-get update && sudo apt-get upgrade

```
to keep wverything up to date

---

### Post by Hippytaff on 2010-10-01
ballsed the formatting up there - hope it still makes sense :-s

---

### Post by plucky on 2010-10-01
> **Hippytaff said:**
> ballsed the formatting up there - hope it still makes sense :-s

You can edit your own posts.Checkout the "edit" button on the bottom right hand side of your posts.

---

### Post by Hippytaff on 2010-10-01
>  
You can edit your own posts.Checkout the "edit" button on the bottom right hand side of your posts.

 
cheers :-)

---

### Post by nothingspecial on 2010-10-01
> **DayLite said:**
> I don't understand what SVN means :confused:
I installed version 0.2.7-1227
Then I added the PPA so I can get all the updates.

I noticed that in the Ubuntu Software Center it tells me Guayadeque is not installed. The version in the Software Center is version: 1262~lucid-1 (guayadeque-svn)

What is the svn stand for? I want to use a stable version. What do I put in the Software sources that will update the stable version when a new one is released. I think I have the wrong one:confused:

This is what I copied to the Software Sources:


Guayadeque is updated through subversion as often as 10 times a day sometimes. The point is that the developer  improves it then the users can tell him of any problems, then he fixes them.

To do that

```
sudo apt-get install subversion build-essential cmake gstreamer0.10-plugins-good gstreamer0.10-plugins-base libwxgtk2.8-dev libtagc0-dev libsqlite3-dev libcurl4-openssl-dev libdbus-1-dev libgstreamer0.10-dev libflac-dev
``````
svn co [http://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk](http://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk) guayadeque
``````
cd guayadeque/
``````
./build
```
```
sudo make install
```Then to update

```
cd guayadeque
make clean
svn up
./build
sudo make install
```The ppa, is for people who don`t want to risk it breaking.

There is a stable version in the 10.10 repositories, but you will not get the new features as quickly, mp3 player support etc, when they become available.

So it`s up to you really.

---

### Post by DayLite on 2010-10-01
Thanks for your support.

---

