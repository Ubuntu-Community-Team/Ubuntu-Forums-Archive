---
title: "[SOLVED] directories?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by aut-omatic on 2008-12-21
hi!,

well, i have been using ubuntu and the terminal for a while now. But when i get instructions, i never understand when people say : go to directory and extract using: eg.:

                       tar zvxf CJLZ600LE-CUPS-1.0-1.TAR.gz

i just never understood if i just go to the file manually and extract it, or if i use the terminal or whatever. This just really confuses me^^.

All help is greatly appreciated :D

---

### Post by aut-omatic on 2008-12-21
P.S.: I would also like to know what it means to "enter a directory".

thank you

---

### Post by ibutho on 2008-12-21
What you need to do is learn a bit about the Linux/Unix command line. The best place to start is [Linux Command]("http://www.linxcommand.org"). If its an option, get yourself a copy of a book called UNIX by Deborah S. Ray and Eric J. Ray.

---

### Post by Elfy on 2008-12-21
Enter a directory would mena change to it, say for instance you have a directory foo on your desktop. When you open your terminal you are in your home, to get to the desktop

```
cd Desktop
```

foo would now be there so you could 

```
cd foo
```

To move directly to foo from home

```
cd Desktop/foo
```

You can use the tab autocomplete - try to change to Desktop - type cd Des then use tab :) , it works for any directory or file

If you wanted to  tar a file in foo you could change to the directory or run it

```
tar zvxf /Desktop/foo/file.tar.gz
```

again you could use tab for those looong filenames.

If you were in a different directory, for instance foo and wanted to return to your home there is a shortcut - it is ~/

So running ```
cd ~/
``` would get you back there.

---

### Post by namdung on 2008-12-21
I usually prefer to right click on the file and select "Extract here".

---

### Post by aut-omatic on 2008-12-21
> 
Code:

cd Desktop

That's exactly what i needed!!! THANKS TO ALL OF YOU :)

---

### Post by Elfy on 2008-12-21
couple fo cheat sheets

[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)
[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

also bear in mind that linux is case sensitive - desktop is not the same as Desktop

---

### Post by gTinker on 2008-12-21
[QUOTE=aut-omatic]P.S.: I would also like to know what it means to "enter a directory".
thank you[/QUOTE]

No one has mentioned it yet but directory is an older term for what are usually called folders these days. You probably would have understood better if you'd seen folder written instead of directory. It's good to understand both ways of referring to locations and sometimes, those of us who understand, forget to explain. Some people have only heard the term folder in their past computing experience.

---

### Post by billgoldberg on 2008-12-21
> **aut-omatic said:**
> hi!,

well, i have been using ubuntu and the terminal for a while now. But when i get instructions, i never understand when people say : go to directory and extract using: eg.:

                       tar zvxf CJLZ600LE-CUPS-1.0-1.TAR.gz

i just never understood if i just go to the file manually and extract it, or if i use the terminal or whatever. This just really confuses me^^.

All help is greatly appreciated :D

I usually just use Nautilus (the file manager) to go to the file and right-click it to extract.

It doesn't matter if you untar it using the cli or the gui.

---

### Post by billgoldberg on 2008-12-21
> **gTinker said:**
> No one has mentioned it yet but directory is an older term for what are usually called folders these days. You probably would have understood better if you'd seen folder written instead of directory. It's good to understand both ways of referring to locations and sometimes, those of us who understand, forget to explain. Some people have only heard the term folder in their past computing experience.

It's not an older term. 

It's the correct term for Linux.

On Windows they are called folders, in Ubuntu they are directories.

I usually use "folders" because it's faster to type and everyone understands what you mean.

---

