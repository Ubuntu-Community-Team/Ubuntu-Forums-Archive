---
title: "Slow file extraction times"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2009-11-13
It might just be me but I find extracting RAR files a lot faster in Windows. Is there any issues around file extracting in Ubuntu? It takes at least double the time to extract a file in Ubuntu than it does in Windows. Seems strange to me, but is anyone else having this problem?

Am running Karmic 9.10 64bit.

Thanks

---

### Post by coldReactive on 2009-11-13
I extract faster in linux than in windows by golly!

Especially with specs like those, you shouldn't be having any troubles.

Are you using unrar from terminal, or are you using xarchiver or file-roller?

---

### Post by Arup on 2009-11-13
Yep something wrong there, extract time are pretty quick, a file like tts.rar which is around 160mb is much faster in Ubuntu than in Windows with my dual quad cores.

---

### Post by terrykiwi83 on 2009-11-13
Only thing I know is that it opens with archive manager, and nope don't use terminal I just right click then select extract here. Yeah I thought with my specs it should be quick but nope takes a good 5 minutes to extract a 700MB set of rar files.

---

### Post by coldReactive on 2009-11-13
> **terrykiwi83 said:**
> takes a good 5 minutes to extract a [SIZE="6"]700MB[/SIZE] set of rar files.

:|

That would take me about 3-5 minutes as well.

---

### Post by terrykiwi83 on 2009-11-13
Only thing is in Windows 7 it does this in less than 2 minutes. When I timed it I think it was a minute and a half.

---

### Post by coldReactive on 2009-11-13
> **terrykiwi83 said:**
> Only thing is in Windows 7 it does this in less than 2 minutes. When I timed it I think it was a minute and a half.

Even worse is that you are comparing it to Windows 7, the newest Microsoft OS.

---

### Post by karimk on 2010-06-22
I am having same problem extremely slow extraction time, gonna try with unrar if it's any better.

I dont get the " you comparing it with MS OS " what is that supposed to mean btw?

EDIT: yes unrar seems to work much better. you gonna need to install it thoough.

sudo apt-get install unrar

once install type:

unrar --help

for a list of all commands and usage.

---

