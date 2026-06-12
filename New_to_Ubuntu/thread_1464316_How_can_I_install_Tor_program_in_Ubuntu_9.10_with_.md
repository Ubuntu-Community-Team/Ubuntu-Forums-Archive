---
title: "How can I install Tor program in Ubuntu 9.10 with out using terminal?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by xgtyca on 2010-04-28
[SIZE=3]Dear All,
How can I install Tor program in Ubuntu 9.10. I saw some ways in different sites but all of them needs to use terminal and I am a very beginner and never used the terminal before
Is there a way to install Tor with graphic interface?:confused::confused::confused:
[/SIZE][SIZE=3]
Thanks[/SIZE]:popcorn:

---

### Post by akand074 on 2010-04-28
Well its already in the repositories so you can use Synaptic Package Manager, but those are old just follow these instructions.

Its honestly very easy and much quicker to do it with the command line.

Heres what to do. First go to System > Administration > Software Sources and choose the "other software tab" and click add. Copy and paste this line there:

```
deb http://deb.torproject.org/torproject.org Karmic main

```Then go to Accessories > Terminal and copy these lines one by one into the terminal

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
apt-get update
apt-get install tor tor-geoipdb


```And your all done. Now you have the latest version of Tor and it will automatically update through Ubuntu's update manager. :)

EDIT: Also it seems you might have to configure it after, check out this link if you do:

[http://www.torproject.org/docs/tor-doc-unix.html.en#polipo](http://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

Everything is explained on the Tor website. Post back if you need a hand. I or someone else could give you a hand. (It is almost 3 in the morning here so I might be asleep and I have an exam tomorrow so good luck!)

---

