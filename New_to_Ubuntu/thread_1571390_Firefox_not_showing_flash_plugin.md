---
title: "Firefox not showing flash plugin"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by bzort on 2010-09-09
I am running an Elonex Webbook with the original OS and Firefox 3.01

Linux xxxxxx 2.6.24-27-generic #1 SMP Wed Mar 24 10:04:52 UTC 2010 i686 GNU/Linux

Flash shockwave simply does not show in the Firefox plugins, neither about:plugins nor Tools -> Add-ons -> Plugins

$ ls -l /usr/lib/adobe-flashplugin/
total 23360
-rwxr-xr-x 1 root root 11950976 2010-09-09 18:57 libflashplayer.so
-rw-r--r-- 1 root root 11934428 2010-07-30 20:49 libflashplayer.so.old

Shows where I renamed the old lib and grabbed a new one from Adobe tarball

ls -l /usr/lib/firefox/plugins/
total 0
lrwxrwxrwx 1 root root 37 2010-09-09 18:24 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

ls -l /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root 44 2010-09-09 18:24 /etc/alternatives/firefox-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so

ls -l /usr/lib/mozilla/plugins/
total 0
lrwxrwxrwx 1 root root 37 2010-09-09 18:24 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

Have I missed something?

Thanks in anticipation

---

### Post by philinux on 2010-09-09
bzort,

```
sudo updatedb

then 

locate libflashplayer.so
```

The first command has no output. Post back what the locate turns up.

---

### Post by Arla on 2010-09-09
Maybe I'm missing something, but did you try installing the flashplugin-installer?

---

### Post by peakshysteria on 2010-09-09
Why don't you start with updating your FF?

---

### Post by lovinglinux on 2010-09-10
Update your system, then get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by peakshysteria on 2010-09-15
> **lovinglinux said:**
> Update your system, then get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Never heard of it. Tried it. Amazed. Works like a charm. Thanks a million man.

---

### Post by lovinglinux on 2010-09-15
> **peakshysteria said:**
> Never heard of it. Tried it. Amazed. Works like a charm. Thanks a million man.

Thanks. I started to develop that extension in May, so most people don't know about it yet. Nevertheless, it has a considerable user base already (~ 5000) and is the second most popular extension I make. The top one is [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/").

---

### Post by mikeydeeeee on 2011-03-06
Excellent!!!

---

