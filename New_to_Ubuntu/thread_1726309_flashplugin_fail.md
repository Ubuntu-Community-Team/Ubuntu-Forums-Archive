---
title: "flashplugin fail"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2011-04-11
I just installed 10.10 on my macbook pro. I did this
```
sudo apt-get install flashplugin-nonfree
``` and it seemed to work just fine except now when i go to a site like youtube, firefox tells me that i have to install flash. so when i try to use firefox to install it, firefox then tells me its already installed. what am i missing here?

---

### Post by wolfen69 on 2011-04-11
Try Flash Aid [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by e1ektrob0y on 2011-04-11
thanks but i'm actually using chrome more than firefox

---

### Post by beew on 2011-04-11
> **e1ektrob0y said:**
> thanks but i'm actually using chrome more than firefox

Doesn't matter. As long as you have firefox installed you can use flash-aid and it would fix it for the whole system.

---

### Post by wolfen69 on 2011-04-11
Remove what flash you have, and get the tar.gz flash file, extract it, and put it in /usr/lib/mozilla/plugins Chrome will share the directory with Firefox. Always works for me. [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect)

---

### Post by gandaran on 2011-04-11
> **e1ektrob0y said:**
> thanks but i'm actually using chrome more than firefox
if you are actually using chrome (not chromium) then update chrome, chrome 32-bits uses built in flash not the system installed flash like firefox
and the correct recommended flash package to install in ubuntu 10.10 is **flashplugin-installe**r not flashplugin-nonfree.

---

