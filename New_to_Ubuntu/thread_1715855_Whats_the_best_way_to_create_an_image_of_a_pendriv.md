---
title: "Whats the best way to create an image of a pendrive?"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by mikee55 on 2011-03-27
I got a USB install of Puppy, how can I copy its Partion?

Mike

I need to install it to another drive of the same size and type. I'm using Ubuntu 10.10 now. Thanks

---

### Post by TeoBigusGeekus on 2011-03-27
Could you explain a bit more?

---

### Post by mikee55 on 2011-03-27
I installed Puppy linux onto a 125mb usb stick, I want to copy it to another usb stick of the same size and type.

Mike:D

---

### Post by aaaaalex on 2011-03-27
The best way would be to use dd. 

Plug in the first drive (lets call it SOURCE) and run fdisk -l to get its device name (e.g. /dev/sdX) then plug in the second drive and also get its device name (e.g. /dev/sdY). 

A simple ```
dd if=/dev/sdX of=/dev/sdY
``` would get you sorted in a couple of minutes. Unfortunatly dd does not produce any output to follow while its working. 

You might consider taking an intermediate step and make an image of your drive in case you need to clone it again later.
```

dd if=/dev/sdX of=$HOME/mypuppyimage.image
``` and then 
```

dd if=$HOME/mypuppyimage.image of=/dev/sdY
```

Its a good idea to have at least a quick glance on the man page of course: man dd. Have not used it in a while so no warraty :-D

EDIT: Of course you may have to sudo some of that ;-)

---

### Post by TeoBigusGeekus on 2011-03-27
Supposing /dev/sdc is the source drive and /dev/sdd is the target drive
```
dd if=/dev/sdc of=/dev/sdd
```
should do it.

---

### Post by mikee55 on 2011-03-27
Hi aaaaalex, I tried to clone first with
 dd if=/dev/sdd of=$HOME/mypuppyimage.image
It said permission denied, I did this from Terminal.

What gives? 

Mike :confused:

---

### Post by aaaaalex on 2011-03-27
sudo? :-D

---

### Post by mikee55 on 2011-03-27
Silly me, I have my Image, thank you.

Thanks for your help.


Mike:D:D:D:D

---

### Post by aaaaalex on 2011-03-27
Well thats great. 

Under Thread Tools just above your first post you can now mark it as SOLVED. :-D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

