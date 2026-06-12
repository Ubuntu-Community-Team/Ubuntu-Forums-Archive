---
title: "Messy GRUB Situation After Installing Windows 7"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-08-15
Hey everyone, I have this laptop that I dualboot Ubuntu 9.04 64 bit and now Windows 7 Pro (from MSDN AA).

I used to have Vista and 9.04. Back when I installed Ubuntu I installed GRUB just to its partition and EasyBCD (on Vista) handed it over to GRUB.

Now Windows 7 steps in off a fresh install and overwrites the MBR. What I want to do is erase GRUB off of my Ubuntu partition and install it fresh for the whole system if that makes sense.

It's probably pretty easy, but I can't find anything in the cloud to help at the moment.

---

### Post by Bölvaður on 2009-08-15
this is by the ubuntuforum user: nixiepixel

[http://www.youtube.com/watch?v=WtBBl6HvdpM]("http://www.youtube.com/watch?v=WtBBl6HvdpM")

---

### Post by Lazy-buntu on 2009-08-15
I used: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to fix my desktop, but that was when it was the head honcho previously.

Will it work in my laptop's situation where it is still on the Ubuntu partition?

---

### Post by Lazy-buntu on 2009-08-15
::facepalm::

I just gave my own link a whirl and it seems to be working. I was afraid to try it because of the preexisting installation.

Sorry for the false alarm. :)

---

### Post by Lazy-buntu on 2009-08-15
Ignore this post, I just went back to the basics: ```
sudo gedit /boot/grub/menu.lst
```

---

