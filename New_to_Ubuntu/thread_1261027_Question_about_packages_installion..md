---
title: "Question about packages installion."
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Mehrdad2009 on 2009-09-08
Hi
I have question about installing packages in ubuntu 9.04.
I have some *.bz2 and *.tar.gz packages but I don't know how I should install these packages.
Please help me.(***_I am really beginer in linux._***)

---

### Post by credobyte on 2009-09-08
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by BadBoy4Live on 2009-09-08
*.bz2 and *.tar.gz ar archives. depending on what your installing i suggest you unpack them in a directory. within the directories you may then find a readme wich could state how you need to install the package/software. if your trying to install a theme or something else, instructions might be different.
Hope this helps a bit

---

### Post by Whiffle on 2009-09-08
Have you searched for these programs in Synaptic?  If they are available there, that is the preferred way to install them ( It can be found under System > Administration )

And what you have there are not really packages, .tar.gz and .bz2 files generally contain source code, which you need to compile first in order to install.  It is much easier to use a .deb package, which is precompiled and ready to go.

---

### Post by egalvan on 2009-09-08
> **Whiffle said:**
> Have you searched for these programs in Synaptic?
  If they are available there, that is the preferred way to install them ( It can be found under System > Administration )

+1 for using Synaptic. If you are that much a beginner, it will save you much grief.

Having said that, I can also say that compiling and/or installing via the command line is an excellent learning experience.
just be aware that "learning experience" is usually synonymous with 'breaking stuff', and be prepared to re-install a few times.
It's what I did (and still do), but I usually used an older machine to practice on.

> 
And what you have there are not really packages, .tar.gz and .bz2 files generally contain source code,
 which you need to compile first in order to install.
  It is much easier to use a .deb package, which is precompiled and ready to go.

.tar .gz .bz2 can contain .deb packages...
so this can be confusing for a beginner,
since the word "package" seems to have several definitions,
depending on the distro :)

And yeah, installing from source can be as easy as typing three or five commands into the terminal...
or a nightmare of cross-dependencies...

---

### Post by chris1950 on 2009-09-08
Don't forget many are also in Applications>Add/Remove.:P

---

