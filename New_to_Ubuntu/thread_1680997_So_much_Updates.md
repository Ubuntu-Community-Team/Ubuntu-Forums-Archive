---
title: "So much Updates"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by alfamud on 2011-02-03
Hi im a user of Ubuntu 10.10, i use Ubuntu all day, but i dual boot to play games, but there is something that is bothering me.
Almost every day Ubuntu has updates available about 50-100 MB its getting very annoying because my internet connection is very slow.

My question is, is it worth it to download all of that, or just ignore them and wait for the new natty narwhal?

Thxs ):P

---

### Post by mlentink on 2011-02-03
Welcome to the free world.

Whether to update or not is totally up to you. You can even turn of the update notification completely if you so desire, though I would recommend against it. 
About the size of the updates: do you only have the standard packages installed or have you added software? Because the update manager doesn't just take care of your OS, but also of all packages installed through the Software Center of synaptic.

---

### Post by ptn107 on 2011-02-03
I'm not using any unofficial update sources and I don't see nearly as many updates as you.  Certainly not daily.  Make sure your /etc/apt/sources.list file contains only the following:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

The amount of updates you get depends on the amount of packages you have installed.

---

### Post by Elfy on 2011-02-03
I've got a few PPAs - 13 - and I don't see that many updates either.

I'd be interested to know what all these updates you are getting 'almost everyday'

---

### Post by candtalan on 2011-02-03
Is your setting in
System>Software Sources>Updates
set for 'Daily'?

You could choose a longer time period, then arrange to leave it running for a long time say over night,  when you will not be using it?

hth

---

