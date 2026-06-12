---
title: "sdl-lib and sdl-lib-dev"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by petersull on 2011-08-05
I want to install QB64, but the install routine tells me I am missing sdl-lib and sdl-lib-dev files and therefore will not run.
I don't have a clue what to do with these files, but I have found the following site where I can download them...

[http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)

Perhaps someone could tell me if this is where I should get them and guide me through what I have to do with them.

I am using Natty 32 bit on a 64 bit laptop.

Thanks in anticipation,

Peter Sullivan.

---

### Post by drpjkurian on 2011-08-05
HI
Since Ubuntu belongs to Debian Stable, Please install those files which has "debian'

---

### Post by petersull on 2011-08-05
Thanks drpjkurian.

I can see the link to the debian ones on the website and will have a go.

Cheers.

---

### Post by oldos2er on 2011-08-05
Install lib files from Ubuntu's repository ```
sudo apt-get install libsdl1.2-dev libsdl1.2debian
```
Ubuntu is based on Debian unstable.

---

