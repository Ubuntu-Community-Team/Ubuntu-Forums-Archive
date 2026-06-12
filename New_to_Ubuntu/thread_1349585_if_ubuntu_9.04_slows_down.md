---
title: "if ubuntu 9.04 slows down"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by al.adab on 2009-12-08
I'm on a fresh install - day two. Ubuntu occasionally slows down, and it didn't happen on the previous install. I'm not running complex applications - graphics and the like - the usual word.doc plus browser. 

Do you know any trick to speed it up? Any way to safely tweak it to prevent it from slowing down?

---

### Post by zkriesse on 2009-12-08
When you say > Ubuntu occasionally slows down, and it didn't happen on the previous install what do you mean by this exactly?

---

### Post by LunaticHiatus on 2009-12-08
whats your computers specs? You could use a lighter ubuntu distro like crunchbang (which is ubuntu based). Or ubuntu minimal + lxde.

---

### Post by al.adab on 2009-12-08
for instance when I'm multi-tasking, like

loading a webpage on Firefox and writing things up on an Open office word.doc and checking my email on Thunderbird and writing an email...the usual routine :) 

all of a sudden I realize that what I'm typing doesn't appear on the word doc or email template so I go back to the web page that's supposedly still loading up but it takes forever to switch from there to Firefox...

---

### Post by al.adab on 2009-12-08
been on Ubuntu 9.04 since it came out on this machine with no speed issues.

---

### Post by booshire on 2009-12-08
You can check to see if any process is bogging things down with the "top" command in a terminal. There are also some graphical versions available somewhere if you want it to look pretty. You might also check your swap (in top) to see if it is filling up.

---

### Post by al.adab on 2009-12-08
ah, the specs: 

Dell (laptop)
2.0GHz Intel Core 2 Duo T7250
Memory: 2GB of 667MHz
Hard drive: 160GB at 5,400rpm
Chipset: Mobile Intel 965 Express
Graphics: 128MB Nvidia GeForce 8400M GS

---

### Post by LunaticHiatus on 2009-12-08
you can check it system monitor for the gui, under the Resources tab to check swap and the Processes for which applications are taking up the majority of the cpu and memory.

---

### Post by LunaticHiatus on 2009-12-08
specs are certainly nice. You should be having no trouble. Whats your cpu usage and memory usage look like when no applications are running?

---

### Post by al.adab on 2009-12-08
plz let me know if you can decode the screenshot of a *sudo top* in attachment.

---

### Post by al.adab on 2009-12-08
sorry the screenshot was taken while the following applications were running: 

firefox
thunderbird
open office writer

---

### Post by al.adab on 2009-12-08
this screenshot was taken while no application was running (well, except for the screenshot...)

---

### Post by al.adab on 2009-12-08
CPU is roughly between 10 and 30% while running the three applications mentioned above

---

### Post by al.adab on 2009-12-08
gnome-system-monitor is between 4 and 15% roughly

---

### Post by LunaticHiatus on 2009-12-08
Your cpu usage for firefox is unreasonably high unless you had a few tabs running, flash running, or have a crapload of extensions. Everything else looks pretty normal to me.
If your just interested in making your desktop lighter. You can lighten it up by using less resource hungry applications (openoffice is pretty fat) for like abiword. Also, extensions can bloat firefox. Depending on the extension it can bloat it significantly. Also, stopping various applications from "startup applications" that you don't use. Like visual assistance, bluetooth, gnome login sound. unless you use or really like those.
If your hardcore, you could also use a lighter desktop like LXDE, or fluxbox.

Sorry I couldn't be of more help...

Oh yeah? Did you upgrade from jaunty to karmic? They DO suggest to do a clean install, but I never found out why. I figure it has to do with the new filesystem and the new grub. Also, doing a clean install with ext4 and grub2 would increase your speed quite a bit.

---

### Post by al.adab on 2009-12-08
Thanks everyone! Going to try out LunaticHiatus's suggestions for sure. Perfectly ok with using AbiWord (which I'm downloading now) and trying out lighter desktops (I suppose as the last resort for the time being). 

In any case, you advise a good alternative to Firefox in this respect? Epiphany, maybe?

---

### Post by LunaticHiatus on 2009-12-08
There are many lighter browsers, people tend to favour one over another based on preference. Chromium, epiphany, konquoror, Kasahakaze (for minimal gecko), and Midori are all good browsers.

---

### Post by lovinglinux on 2009-12-08
> **al.adab said:**
> Thanks everyone! Going to try out LunaticHiatus's suggestions for sure. Perfectly ok with using AbiWord (which I'm downloading now) and trying out lighter desktops (I suppose as the last resort for the time being). 

In any case, you advise a good alternative to Firefox in this respect? Epiphany, maybe?

Instead of searching for a Firefox alternative, start it in safe mode and check if you have the same problem. If not, then most likely that you have an extension leaking memory or a web site using too much CPU (flash, javascript).

```
firefox -safe-mode
```

To boost Firefox performance, I recommend a database optimization. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for instructions.

---

