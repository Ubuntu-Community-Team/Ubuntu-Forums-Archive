---
title: "vim installation in 10.10"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by kni8 on 2011-04-10
Hi,there. I have downloaded vim 7.3 zipped file and tried installing with almost all executable file but none of them helping me to install it to system. i know "apt vim -full" get vim downloaded to system. But i don't have access to internet from my pc. Could anyone help me with the issue. I'm a newbbie linux user.

---

### Post by TeoBigusGeekus on 2011-04-10
Where did you download it from?

As a personal advice, I would suggest to install gvim instead of vim, but still use gvim's command line editor. Gvim supports clipboard buffers, but not vim.

---

### Post by kni8 on 2011-04-10
from vim.org. Gvim means gnome vim right? could you provide me with the download link, if you don't mind.

---

### Post by TeoBigusGeekus on 2011-04-10
Gvim (gnome-vim) has a gtk frontend for vim, ie. you can not only use it from command line but also with a gui (sacriledge if you ask me).

The thing with vim nowadays, is that it's compiled without support for your system's clipboard. That means that you can't copy or paste text/code from or to vim.

Gvim installs its own version of vim, which supports X and system clipboard (middle click copy or right click copy). Install gvim and run it as you would run vim, ie. give 
```
vim file.ext
```
from command line.

Once in there, you can give
```
gg"+yGG
```
to copy an entire file into your clipboard and paste it anywhere with right click>paste (with gg"*yG you would paste it with middle click).

---

### Post by kni8 on 2011-04-10
oh! Thanks for the info. i will give try and let you know the outcome.

---

### Post by kni8 on 2011-04-10
got a problem. As i mentioned above i don't have access to internet from pc. I googled for gvim download and reached the page listing package details. i don't know which one to choose from. My pc run on amd processer with ubuntu 10.10

---

### Post by TeoBigusGeekus on 2011-04-10
Check out [this]("http://packages.ubuntu.com/maverick/vim-gnome") page (if you're using maverick).

Watch out for the dependencies though (the packages with the red dot).
There seem to be quite a few...

---

