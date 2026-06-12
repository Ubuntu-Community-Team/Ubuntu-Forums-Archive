---
title: "Setting up Lives"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by BZF on 2009-05-11
[FONT=Arial][SIZE=1][COLOR=Blue]What are the codes I do in terminal to install the video editing program called Lives? I need help because it uses a different process than normal. I have the folder downloaded I just need to install
[/COLOR][/SIZE][/FONT]

---

### Post by ashmew2 on 2009-05-11
Hi , IMO , 
Just go here : 
[http://www.xs4all.nl/%7Esalsaman/lives/current/LiVES-0.9.9.8.tar.gz]("http://www.xs4all.nl/%7Esalsaman/lives/current/LiVES-0.9.9.8.tar.gz")

Download the tar.gz file for LiVes. Download the file to your Desktop.
Go into a terminal and type this (one at a time):

```
sudo apt-get install libgtk2.0-dev build-essential jackd libjack-dev sox mplayer


cd ~/Desktop
tar -xvf LiVES-0.9.9.8.tar.gz
cd LiVES-0.9.9.8
./configure

```The ./configure command will check your system for any missing files/packages that you need to install LiVes on your system. Just let it successfully finish. And after that :

```
make

sudo make install
```Basically , we've compiled the package from source after installing all of its dependencies.Just reply back if you run into any problems ;)

This will make you a basic install which should be more or less fully functional.There might be an error here or there about some missing files maybe , so you can just post here and we'll see what can be done :)

PS - Could you use a bigger font next time ? :P

---

### Post by gandaran on 2009-05-11
get a ready lives .deb package from [getdeb here]("http://www.getdeb.net/category.php?id=12") to install double click the package and hit install button

---

### Post by ashmew2 on 2009-05-11
> **gandaran said:**
> get a ready lives .deb package from [getdeb here]("http://www.getdeb.net/category.php?id=12") to install double click the package and hit install button

I thought it wasnt out yet ;)

---

### Post by t0p on 2009-05-11
What you want to do is called *compiling*.  One problem often encountered when compiling software for your machine is that of *missing dependencies* - that is, other programs that need to already be present in order to make the new one work.  [This guide]("https://help.ubuntu.com/community/CompilingEasyHowTo") is very good, as it explains the process of fulfilling dependencies so your compilation will work.

---

