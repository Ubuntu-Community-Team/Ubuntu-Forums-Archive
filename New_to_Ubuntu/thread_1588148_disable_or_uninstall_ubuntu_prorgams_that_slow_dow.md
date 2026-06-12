---
title: "disable or uninstall ubuntu prorgams that slow down the system"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by northwestuntu on 2010-10-04
ive searched on it before, but never really find a certain answer. stuff like gwibber and evolution can you uninstall that or disable it on startup?

i really have no need for stuff like that so hate to be wasting memory or cpu on that.  

ive heard minimal install but dont really want the hassle.  i like the base of ubuntu, just want to cut out all the background stuff going on. 
:popcorn:

---

### Post by pricetech on 2010-10-04
You should be able to remove anything you don't want through Synaptic Package Manager.

---

### Post by oldos2er on 2010-10-04
Go to System, Preferences, Startup Applications, uncheck what you don't want automatically started.

---

### Post by northwestuntu on 2010-10-04
from what i have read though evolution is part of the ubuntu system and it's not a good idea to uninstall.

---

### Post by emoguitarist06 on 2010-10-04
> **oldos2er said:**
> Go to System, Preferences, Startup Applications, uncheck what you don't want automatically started.

exactly what I would say

---

### Post by northwestuntu on 2010-10-04
so maybe go with disable rather then uninstall.

---

### Post by andrewthomas on 2010-10-04
> **northwestuntu said:**
> from what i have read though evolution is part of the ubuntu system and it's not a good idea to uninstall.
If you don't use it you can uninstall it.  It is just a dependency of the meta-package ubuntu-desktop.  

When in doubt

use 

```
aptitude why packagename
```

---

### Post by northwestuntu on 2010-10-04
> **andrewthomas said:**
> If you don't use it you can uninstall it.  It is just a dependency of the meta-package ubuntu-desktop.  

When in doubt

use 

```
aptitude why packagename
```


so i could use

aptitude why evolution ?

---

### Post by bodhi.zazen on 2010-10-04
It is far easier and you end up with a faster system if you start minimal and add only what you need.

You could start with lubuntu and add or a minimal install

If you want to add gnome, install gnome and not ubuntu-desktop. Samd for kde/kubuntu-desktop or xcfe/xubuntu desktop.

---

### Post by lobralleo on 2010-10-04
I removed Evolution myself without any noticeable problem.
Typically, when removing packages you might have to keep some libraries shared with other applications, but otherwise you can pretty much clean up your system the way you like it.
By using Synaptic or apt-get, you will be notified about dependencies to be removed and the like, so you can always check before damaging your system.

---

### Post by northwestuntu on 2010-10-04
> **bodhi.zazen said:**
> It is far easier and you end up with a faster system if you start minimal and add only what you need.

You could start with lubuntu and add or a minimal install

If you want to add gnome, install gnome and not ubuntu-desktop. Samd for kde/kubuntu-desktop or xcfe/xubuntu desktop.

i might try the minimal install and see if i can get it to work. sounds like thats what i really need to do.

---

### Post by mike555 on 2010-10-04
Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

---

### Post by northwestuntu on 2010-10-04
> **mike555 said:**
> Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

thanks for the list :P

---

### Post by UbuNoob001 on 2010-11-20
> **northwestuntu said:**
> i might try the minimal install and see if i can get it to work. sounds like thats what i really need to do.

While this thread is old(ish), just wanted to make a comment: 

I was in the same situation. Ubuntu Minimal is really quite easy to set up. The following has worked great for me: 

```
ubuntu 10.04 minimal + gnome-core + gdm + gnome-system-tools + wicd + gnome-screensaver + file-roller+ pcmanfm
```then, on top of that I have added: ```
vlc + chromium-browser 
```you will know what you need simply by using it as you normally would then whenever you think "where the hell is X" install X or a similar but faster program with fewer dependencies. 

getting to use aptitude has been rather easy and a pleasure and, with just a little bit of perspective change, becomes as easy as "software center" or synaptic. 

once you add some art/themes you wont even know your not using 10.xx desktop.

---

### Post by germanix on 2010-11-20
Hi Mike555, I have just followed the advice you gave Northwestuntu with the exception that I did not remove: espeak, g-brainy or indicator-messages. Problem is on re-boot I now have no panels and do not know how to get them back. At the moment I can do nothing. Any ideas?

---

