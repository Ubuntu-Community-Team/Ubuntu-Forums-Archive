---
title: "a problem with findutils and installing"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by skityl on 2009-01-19
Hello! I am an absolute beginner so I imagine that my mistake here is really obvious, and (hopefully) easy to fix.

I want to install a Ralink driver for my wireless adapter. Turns out that I need 'build-essential' for that. So I downloaded it and apparently I need something called 'libc6-dev'. I found that and tried to install it, but I require 'libc6'.

But to install libc6, I need 'findutils'; But I already have findutils! And it's still not letting me install. (I've tried reinstalling findutils, to no avail)

For what it's worth, the error message I get is:
"Error: Dependency is not satisfiable: findutils"

I've searched far and wide to find a solution to this problem, but so far there's been nothing.

What I've seen of Ubuntu so far I've been very impressed with, and I would love to convert entirely. So any help here would be greatly appreciated.

---

### Post by Partyboi2 on 2009-01-19
If you are able to connect the machine to the internet using ethernet you can open a terminal (Applications>Accessories>Terminal) and install build-essential by typing
```
sudo apt-get install build-essential
``` this will take care of all the dependencies like libc6-dev etc

If you cannot get access to the internet then you can use a ubuntu cd to install it which can be done by opening a terminal and inserting the cd into the cdrom and typing

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by 3rdalbum on 2009-01-19
Is that the entire error message?

I believe there's a later version of libc6 that you have probably downloaded, and this version depends on a later version of findutils too - later than the one you already have.

My best advice would be to take your computer to your broadband router and plug it in physically to the router's Ethernet port. That way Ubuntu will be able to satisfy all the dependencies and install all updates, without you having to constantly go back and forth with packages to get things working.

---

### Post by skityl on 2009-01-19
Thankyou! I got it working!

(except I screwed up the graphics driver install, but I'm just happy that something finally went right)

---

