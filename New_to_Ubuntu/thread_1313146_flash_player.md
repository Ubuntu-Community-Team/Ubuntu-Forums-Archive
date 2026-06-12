---
title: "flash player"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by taken from there on 2009-11-03
I have ubuntu 9.04

I went on macromedia website to install flash player. I did talk to a technician who did have the same version (as he did told me) then me on my computer. My flash player doesnt work properly but his, as he told me is working on his and we did the same thing with the same program on the same ubuntu version. Why is my flashplayer does not work properly? what should I do from now, step by step?

---

### Post by Tyke91 on 2009-11-03
To install the flash player plugin, i usually go here [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP) . Make sure that you haven't got swfdec or gnash installed as those might be used instead of adobe's flash player (adobe owns flash now, not macromedia).

you want to download the .deb file for ubuntu 8.04+

---

### Post by mrboojive on 2009-11-03
You can also try installing from the repositories. Just go to a terminal and type```
sudo apt-get install flashplugin-installer
```

---

### Post by Norm24 on 2009-11-03
Go to Synaptic and install:
```
flashplugin-nonfree
```

This is the very latest.

---

### Post by mrboojive on 2009-11-03
flashplugin-nonfree is a meta-package that installs the flashplugin-installer package. I think flashplugin-installer is the preferred package to install now.

---

