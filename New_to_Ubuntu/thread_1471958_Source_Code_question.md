---
title: "Source Code question"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-05-03
how do i begin editing the source code of ubuntu so i can customize it? For instance my friend has an imbedded terminal constantly running. He told me he did this by editing the source code. 

thanks in advance

---

### Post by nmccrina on 2010-05-04
Well, Ubuntu is basically a conglomeration of many different programs. You can get the source code for any particular program by googling for its homepage, or I think you can install the -src package through Synaptic. For example, you can go to kernel.org to get the actual operating system code, gnome.org forgnome stuff like Rhythmbox, or gnu.org for compilers and lots of utilities. 

Do you know any programming languages? I don't want to dissuade you, but I will warn you that modifying the source code of any of the programs you use a lot will be a pretty arduous task :) You might want to try writing some of your own simple programs first.

---

### Post by 3rdalbum on 2010-05-04
> **Extract_Here said:**
> how do i begin editing the source code of ubuntu so i can customize it? For instance my friend has an imbedded terminal constantly running. He told me he did this by editing the source code. 

He didn't edit the source code of anything to make this happen. It's something you can just add by installing gDesklets (and there are probably other programs that let you do it too).

Also there's no one clump of code that is "Ubuntu". Ubuntu is a collection of programs and projects, each of which you can download and edit the source code for. Note that you would need to compile the source code as well before it becomes used.

You can download the source code for a particular package by typing:

```
sudo apt-get source <packagename>
```

---

