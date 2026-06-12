---
title: "youtube isn't responding to clicks?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Syppli on 2010-02-06
when i use youtube, it seems like pause and play only works sometimes, does anybody know why?

---

### Post by wojox on 2010-02-06
Cause it's youtube. :D Try opening you favourite media player and using it. ;)

---

### Post by s.fox on 2010-02-06
> **Syppli said:**
> when i use youtube, it seems like pause and play only works sometimes, does anybody know why?

Hello,

Which browser are you using? 

-Silver Fox

---

### Post by Syppli on 2010-02-06
> **Silver_fox_ said:**
> Hello,

Which browser are you using? 

-Silver Fox


firefox..

---

### Post by eriktheblu on 2010-02-06
There is some sort of conflict with Flash and Compiz.

The expedient solution is to disable the visual effects.

---

### Post by samantha_ on 2010-02-06
[http://ubuntuforums.org/showthread.php?t=1397907](http://ubuntuforums.org/showthread.php?t=1397907)

If you think is the flash/compiz issue, see my post in that thread.
Otherwise, try the solution that is right under that post.

---

### Post by tom.swartz07 on 2010-02-06
> **Syppli said:**
> when i use youtube, it seems like pause and play only works sometimes, does anybody know why?

> **samantha_ said:**
> [http://ubuntuforums.org/showthread.php?t=1397907](http://ubuntuforums.org/showthread.php?t=1397907)

If you think is the flash/compiz issue, see my post in that thread.
Otherwise, try the solution that is right under that post.

99% of the time, I see this happening with 64bit systems.


Before you start, remove all of the third-party flash packages from synaptic, in particular- swfdec and gnash players. They are probably the ones that are causing the problem in the first place. Theyre good, but theyre not 100% working just yet.

Download the new flash plug-in @ [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Extract the archive from the download link above.
Close all browsers.
Hit ALT+F2 and type
```
gksu nautilus /usr/lib/flashplugin-installer
```
This will open up a new window.
Copy and paste the extracted libflashplayer.so file into this folder, overwriting the current version.
If you have Firefox installed you will also need to install the plugin to the following folder. 
Hit Alt+F2 and type
```
gksu nautilus /usr/lib/mozilla/plugins
```
Paste the same file into this folder, again agreeing to overwrite the current version 

Theres a PPA if you want to use it to keep your flash updated
```
sudo add-apt-repository ppa:sevenmachines/flash
```
If you are still having problems, update it with 
```
sudo apt-get update && sudo apt-get install flashplugin64-installer
```

---

