---
title: "GVIM configuration"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Sholto on 2010-06-02
I have installed gvim, and note it went into /usr/bin. On Windows it goes into a Vim folder which has sub-folders containing various .vim files (such as for colours), and I note that vim does the same (it goes into /usr/share/vim, with these sub-folders). There are no such sub-folders under /usr/bin, and I cannot see where gvim would get its configuration files from.
I have my own colour and other schemes I would like to transfer from Windows. Does anyone know where one would put them so they are automatically sourced by gvim?
Also, where should one put the .vimrc file - in one's home folder, or somewhere else?

---

### Post by Brandon Williams on 2010-06-02
.vimrc is expected to be in your home directory.

Also in your home directory, you can create a directory called .vim with subdirectories for the various extension file types: plugin, syntax, colors, etc.

---

