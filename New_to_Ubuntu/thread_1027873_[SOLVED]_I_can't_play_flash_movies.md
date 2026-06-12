---
title: "[SOLVED] I can't play flash movies"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by retskrad on 2009-01-01
When I search for a movie, it loads and I can see the movie. It goes a couple of secodnds (while having no sounds, just movie) and then it stops, but the movie keeps loading. When I move the pointed forward, the movie plays a couple of seconds (with no sound) and then stops again.

I have flash 10 and ubuntu 8.10. What's going on????

Here is a pic:

I have tried with serveral movies, always the same.

Any help would be appreciated.

---

### Post by joukez on 2009-01-01
Did you install ubuntu restricted extras? [http://help.ubuntu.com/community/RestrictedFormats]("http://help.ubuntu.com/community/RestrictedFormats")

---

### Post by retskrad on 2009-01-01
I wrote "sudo aptitude update && sudo aptitude install ubuntu-restricted-extras" in a terminal.

---

### Post by evilkastel on 2009-01-01
Just in case, Type ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by retskrad on 2009-01-01
It says that I already got the latest version.

---

### Post by RomeReactor on 2009-01-01
Hi. Have you tried emptying Firefox's cache and loading the video again? Which version of Ubuntu are you running--32 bit or 64? Please post the output of:
```
uname -m
```

---

### Post by retskrad on 2009-01-01
Here
> [QUOTE]admin2@ubuntu:~$ uname -m
i686
admin2@ubuntu:~$ 


---

### Post by RomeReactor on 2009-01-01
Does the problem happen with only this video? Did you try emptying the cache and loading the video again? Can you give us more details about your system--CPU, RAM, video card?

---

### Post by retskrad on 2009-01-01
I tried a porn site, they show the videos in flash, and both flash and video worked there..

---

### Post by retskrad on 2009-01-01
Lol, I cleanesd the cache, and it works now.

---

