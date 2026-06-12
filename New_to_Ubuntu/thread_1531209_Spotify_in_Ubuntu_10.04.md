---
title: "Spotify in Ubuntu 10.04"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by lunacia on 2010-07-14
So, I was quite excited when I found out that I could finally run Spotify on my old laptop (can't handle Wine), and followed the instructions:

[http://www.spotify.com/no/download/previews/](http://www.spotify.com/no/download/previews/)

But I can't get it to work... If I try to install it from the Ubutu Software Centre I get the following error message:

> **Package dependencies cannot be resolved**

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

I seem to need package gconf2 2.28.1-0ubuntu1, but I have no ide howto install it... I have tried sudo apt install, but get:

> sudo apt-get install gconf2 2.28.1-0ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gconf2 is already the newest version.
E: Couldn't find package 2.28.1-0ubuntu1


Nor can I find it in Synaptic Package Manager...

Help?

---

