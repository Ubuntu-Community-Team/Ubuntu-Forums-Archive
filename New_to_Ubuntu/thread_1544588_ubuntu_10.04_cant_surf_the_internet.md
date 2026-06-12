---
title: "ubuntu 10.04 cant surf the internet"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Bugsy_malone 666 on 2010-08-02
Hi, I'm new to linux and have just started to play with ubuntu.

started off months ago with 8.04, installed on to a machine (desktop) and it was great, then 9.04, then 9.10 and I sort of installed this to play with but when I got to 9.10 I had issues with network connectivity, then I got some drivers and that was ok.

So then I now have a Lenovo X61s Laptop which I used 9.04 to set the machine up with and then upgraded to 9.10 then 10.04 (thinking it would be best to start off by updating everything as far as I can before I start playing and learning)

so the machine can see my wireless network, I downloaded the 10.04 upgrade through it (taking over 3 hours :O ) then I can download software through the software centre meaning it can use the wireless network, but for some reason it wont surf the internet?

I open firefox (think its 3.6) and it just says it has problems connecting to the server or that it cant find it or that its taking to long.

I am brand new to linux so I have no idea what I am doing yet (I write this from my windows 7 desktop PC)

Any helpers and pointers for a newbie :)

---

### Post by TheNerdAL on 2010-08-02
Just to make sure it isn't the internet, but the browser, try installing Chromium from the Ubuntu Software Center. If you can't then try giving us the output of this: 
```
lspci -v | less

```

Or this for a USB device that you may use to access the internet: 
```
lsusb
```

---

### Post by Bugsy_malone 666 on 2010-08-02
Ah ha!

I did have a look thought software and didnt really find different browsers the first time, but installing google chrome seems to work at a normal speed on the internet.

I did find it a bit odd that firefox that is shipped with 10.04 didnt work yet everything else did!


Cheers for your help :)

Question now is why doesnt firefox work?

---

### Post by RMuscaritolo on 2010-08-02
> **Bugsy_malone 666 said:**
> Ah ha!

Question now is why doesnt firefox work?

Lol, yes young grasshopper. Thats a good question... though, part of the Linux motto is to do it yourself. 

Why not poke around a bit with it. Try to find out exactly what is not working and what still is. You may surprise yourself with what you can find out on your own.

And of course if none of your issues make any sense. You could always just uninstall and re-install Firefox. (But thats not very fun)

Let us know what you find out and we'll see what we can do.

---

### Post by TheNerdAL on 2010-08-02
What version of Firefox are you using?

---

### Post by Bugsy_malone 666 on 2010-08-02
3.6.8

---

### Post by TheNerdAL on 2010-08-02
> **Bugsy_malone 666 said:**
> 3.6.8

When you try to go to let's say [www.google.com](www.google.com), what error does it give you?

---

### Post by Bugsy_malone 666 on 2010-08-02
> **RMuscaritolo said:**
> Lol, yes young grasshopper. Thats a good question... though, part of the Linux motto is to do it yourself. 

Why not poke around a bit with it. Try to find out exactly what is not working and what still is. You may surprise yourself with what you can find out on your own.

And of course if none of your issues make any sense. You could always just uninstall and re-install Firefox. (But thats not very fun)

Let us know what you find out and we'll see what we can do.

well I guess I havent really been that bothered to play with it, just a few things I want to work, then I can play with and break the rest!

Like I need to find out how to make it run emulators and act like an Amiga, I also want to see what music software there is etc

but primarily a working internet connection is the first key!

---

### Post by Bugsy_malone 666 on 2010-08-02
> **TheNerdAL said:**
> When you try to go to let's say [www.google.com]("http://www.google.com"), what error does it give you?

It says 'Unable to Connect'

'Firefox cant establish a connection to the server at  [www.google.com](www.google.com). 

The site could be temporarily unavailable or too busy, try again in a few moments.

if you are unable to load any pages check your computers network connection. 

if your computer network is protected by a firewall or proxy make sure firefox is permitted to access the web'

---

### Post by Bugsy_malone 666 on 2010-08-03
ok tonight I found out that its got to be something to do with the network settings and the router in our house.

Decided to take the laptop to the g/fs house to use her slightly faster net connection and both firefox and emesene worked fine, now I am back home neither work!

its got to be something to do with the way those 2 apps access the web, yet chromium works absolutely fine!

---

