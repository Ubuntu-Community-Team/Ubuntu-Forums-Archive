---
title: "Music player open when selecting a file from places"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by IIIsolitaireIII on 2010-12-14
Hi people,

Am completely new to Ubuntu/Linux coming from running Windows OS all my computer life. I'm also new to these forums *waves*

I wanted to try a new OS and decided on Ubuntu 10.10 64bit. Everything has been running great and I'm slowly getting used to it.

Until today.

Its only a small problem, but a annoying one at that. Every time I select "places-Home folder/Documents/music/pictures/videos/downloads" from the top panel, the Rythmbox music player opens up.

Is there a way to fix this?

Thanks in advance for the help

---

### Post by john77eipe on 2010-12-14
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1631961](http://ubuntuforums.org/showthread.php?t=1631961)

---

### Post by john77eipe on 2010-12-14
In short this is the solution:
```
gedit ~/.local/share/applications/mimeapps.list
```

Find the line inode/directory= and either delete the whole line or add to front.
```
nautilus-folder-handler.desktop;
```

---

### Post by IIIsolitaireIII on 2010-12-14
thanks for the help, its now working again :-D

---

### Post by soluckytouselinux on 2011-03-10
Hi everyone. This fix worked for me. thanks everyone!!

---

