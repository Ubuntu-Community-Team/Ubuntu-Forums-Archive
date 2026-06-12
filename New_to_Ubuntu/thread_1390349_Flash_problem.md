---
title: "Flash problem"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by ben618 on 2010-01-25
Hi everyone

First I'd like to say what an amzing operating system Ubuntu is. I wish I had known about it ages ago :)

Usually when I have problems I find the answers here, but I cant find anything for this:
I use firefox and have trouble on lots of flash based sites. Synaptic package manager shows that I already have flashplugin-nonfree.
Is there anything I can do about this, or does GNU/Linux development of these just take longer? I notice that on the adobe website, the latest version is 8.10, and I am using 9.10 64-bit
To clarify, flash works but only sometimes, and it is often on newer sites where firefox has trouble.

Thanks in advance

---

### Post by tom.swartz07 on 2010-01-25
> **ben618 said:**
> Hi everyone

First I'd like to say what an amzing operating system Ubuntu is. I wish I had known about it ages ago :)

Usually when I have problems I find the answers here, but I cant find anything for this:
I use firefox and have trouble on lots of flash based sites. Synaptic package manager shows that I already have flashplugin-nonfree.
Is there anything I can do about this, or does GNU/Linux development of these just take longer? I notice that on the adobe website, the latest version is 8.10, and I am using 9.10 64-bit
To clarify, flash works but only sometimes, and it is often on newer sites where firefox has trouble.

Thanks in advance

Yep- thats a bug, but its super easy to fix.

Before you start, remove all of the third-party flash packages from synaptic (system>administration>synaptic package manager), in particular- swfdec and gnash players. You could search for them on the top bar.



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


Hope this helps!

Good luck!

---

### Post by tom.swartz07 on 2010-01-25
Post back and let us know if it worked!
If so, please mark the thread as [solved] from the thread tools also.

Thanks!

---

### Post by ben618 on 2010-01-25
Thanks so much for your help
I just went through it, and flash is working great now
Thanks a lot!

---

### Post by texaswriter on 2010-01-25
I see this thread is solved, just wanted to ask if that was a bug with 64-bit Karmic... I have 32-bit Karmic on laptop and haven't had a problem [so far] with flash... Wanted to know if it is in store... lol

---

### Post by tom.swartz07 on 2010-01-25
> **texaswriter said:**
> I see this thread is solved, just wanted to ask if that was a bug with 64-bit Karmic... I have 32-bit Karmic on laptop and haven't had a problem [so far] with flash... Wanted to know if it is in store... lol

Yeah, the only version thats available in the Repos is the 32-bit version, and its 'ported' for use on x64 systems. If you follow that method, it installs the 'official' flash for x64 systems.


Its not too big of a deal using the repo version, but it gets annoying when you cant click on things sometimes. :lolflag:

Have fun!

---

### Post by texaswriter on 2010-01-25
Ah, k, thanks. I'll remember that when I upgrade my desktop processor, which will definitely go 64-bit [gotta change with the times :confused:]

---

