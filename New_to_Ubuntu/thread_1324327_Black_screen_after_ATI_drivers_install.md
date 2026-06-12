---
title: "Black screen after ATI drivers install"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by HarisGR on 2009-11-12
Hello to all. :) New at the community and first post here.

I recently installed ubuntu 9.10 on a [Toshiba Satellite A300-231]("http://www.fotofabrikas.lt/en/items/Toshiba/Notebook/df48cd.4-Toshiba-Satellite-A300-231.html#spec-box-and-cont"). All went well, until I decided to install the ATI drivers (ati-driver-installer-9-10-x86.x86_64.run). When the laptop boots, just after the loading screen, it hangs with a black screen so I can't login.

I searched for a solution online but it seems I can't find one.

Is there any way to fix this problem from the recovery mode?

p.s. found a solution but it demads a change in xorg.conf. When I opened the file, it was completely empty...

---

### Post by HarisGR on 2009-11-12
Just found an answer in this forum but I still have a problem. I found this post:

> **Scott M. Sanders said:**
> Anyway, boot Ubuntu in recovery mode, drop to terminal, login to root, and type in "aptitude." This will give you a text-based package manager like the Synaptic GUI. From here, the offending ATI packages can be found and removed from under Misc. Press ? for help. This should ultimately get you back; it did me anyway after days of guessing. Reply with any questions.

I did all that, but I'm having trouble in locating the installed drivers. Can someone point exactly for what file name to look? While I found many packages (for example "installation-guide-amd64", "xsever-xorg-video-ati" etc.) I don't know which of them I must delete.


(Sorry for double posting, I'm kinda noob in Linux and I'm a little worried)

---

### Post by coffeecat on 2009-11-12
The black screen is an issue some people have been seeing with certain ATI cards when they install the ATI driver and enable compiz.

The simple workaround is to disable compiz. If you don't know what this is, go to System > Preferences > Appearance and click on the Visual Effects tab. Now tick the 'None' box. That should give you your desktop back, but you lose the clever eye candy.

There is a better fix which should let you continue to use compiz in post #9 in this thread:

[http://ubuntuforums.org/showthread.php?t=1316902](http://ubuntuforums.org/showthread.php?t=1316902)

It's fairly easy to follow. The only amendment I would make is, instead of:

```
sudo gedit /etc/X11/xorg.conf
```... use ...

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by HarisGR on 2009-11-12
> **coffeecat said:**
> The black screen is an issue some people have been seeing with certain ATI cards when they install the ATI driver and enable compiz.

The simple workaround is to disable compiz. If you don't know what this is, go to System > Preferences > Appearance and click on the Visual Effects tab. Now tick the 'None' box. That should give you your desktop back, but you lose the clever eye candy.

There is a better fix which should let you continue to use compiz in post #9 in this thread:

[http://ubuntuforums.org/showthread.php?t=1316902](http://ubuntuforums.org/showthread.php?t=1316902)

It's fairly easy to follow. The only amendment I would make is, instead of:

```
sudo gedit /etc/X11/xorg.conf
```... use ...

```
gksudo gedit /etc/X11/xorg.conf
```

Thanks for answering.

The one thing is that compiz was never enabled (no drivers for the card -> it could not enable the visual effects).
The other is that I can't get into gnome or kde. Just before the login screen, it just freezes with a black screen.

---

### Post by coffeecat on 2009-11-12
> **HarisGR said:**
> Just before the login screen, it just freezes with a black screen.

My apologies. I carelessly misread your original post. I'll have a look in Synaptic and see if I can determine which packages you can safely uninstall as per your second post.

**Edit:** sorry, no. I'd better leave this to someone who has installed the proprietary driver with the ati*.run installer as you have done.

---

### Post by HarisGR on 2009-11-12
> **coffeecat said:**
> My apologies. I carelessly misread your original post. I'll have a look in Synaptic and see if I can determine which packages you can safely uninstall as per your second post.

**Edit:** sorry, no. I'd better leave this to someone who has installed the proprietary driver with the ati*.run installer as you have done.

No worries. Thank you very much. :)

---

### Post by coffeecat on 2009-11-12
Rather bizarrely, I think I just came across the answer while aimlessly wandering through some of the other threads. Someone posted this link:

[http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html](http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html)

Of the two commands, the first removes the proprietary ati driver, and the second reconfigures the xserver - which seems to be what you need. I'm puzzled as to why the author seems to think sudo is necessary when one has root privileges in recovery mode - but there you are. :?

Anyway, offered on a no-guarantee, I take-no-responsibilty basis. :p

---

