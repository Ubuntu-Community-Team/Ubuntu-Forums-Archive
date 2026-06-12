---
title: "Vim Xubuntu"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by bilgee0629 on 2011-01-18
Hello! I'm using Xubuntu 10.04 . I've been tryin to install coloscheme on vim. I copied colorscheme file to ~/.vim/colors but when i type :colorscheme gentooish. Vim cannot find the theme. Should i write anything in .vimrc file?

---

### Post by gmargo on 2011-01-18
What **vim** packages do you have installed?  vim is available in multiple versions.  The default version is a rather crippled one named **vim-tiny**.

Install the **vim-gtk** package, and you'll have a full featured version for both gui and command line.  You don't even have to uninstall vim-tiny.

---

