---
title: "Could anyone compile firefox 3.5 for me"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by azotyp on 2009-07-02
Hi I installed firefox 3.5 using method found on the net, but I couldnt install Polish language, so I found Polish firefox 3.5 but it need to be compiled. Could anyone be so kind and compile it for me. I need a .deb for 32 bit ubuntu . Here's the ling to file that need to be compiled
[http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=pl](http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=pl)

---

### Post by hyperdude111 on 2009-07-02
I dont know how but you can install firefox 3.5 like this:

Method 1:
> wget -O - [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2) | tar xj -C ~
This is only a single terminal command but the speed is not optimized you probable wont notice but if you want this guide [http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html) explains how to optimize.

Chose which one you want.

---

### Post by azotyp on 2009-07-02
As I said earlier I tried this eaven from this tutorial and installed english version. But would like to install language and dictionary of my country. But don't know how, so I thought that I could compile version that is allready made with language and dictionary of my country.

---

### Post by Joeb454 on 2009-07-02
Mozilla offer the precompiled version of firefox 3.5 if that's what you're after.

[http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=pl](http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=pl)

That should take you to download it :)

---

### Post by motang on 2009-07-02
I think what azotyp wants is a .deb file or an update from the repos.

---

### Post by lovinglinux on 2009-07-02
If you want to compile yourself, I have setup a tutorial at the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Scroll down to "Compiling Firefox" section. It's not complicated as it seems. For instance, this is the first time I have compiled it. 

BTW, I've got 30% performance boost after compiling it with optimizations for my processor. ;)

---

