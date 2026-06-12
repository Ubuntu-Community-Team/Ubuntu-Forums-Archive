---
title: "Help with links please"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by edpatterson on 2009-06-06
Greetings,

I need some help with links (symbolic?). What I am trying to do is have a file (the link) with the same name just different case as an existing file.

Why? Well, I am trying to learn jpgraph and some of the font associations in the configuration have the case one way and they are stored on my system another. comic.ttf -> Comic.ttf. I tried 'lk comic.ttf Comic.ttf' and ended up with a comic.ttf file of the same size as the original Comic.ttf.

Now this is real lame but I do not know how else to put it. There are some links in the msttcorefonts which show up blue in my terminal. The one I tried to make is white.

Laughing is welcome as long as it is accompanied with an answer.

Searching the forums with symbolic, link and 'blue file' was an exercise in frustration.

Ed

---

### Post by jbruced on 2009-06-06
Not sure exactly what you mean, but links will show up a different color in the terminal. It is a different file type. 

Sound files purple etc...

---

### Post by lloyd_b on 2009-06-06
> **edpatterson said:**
> Greetings,

I need some help with links (symbolic?). What I am trying to do is have a file (the link) with the same name just different case as an existing file.

Why? Well, I am trying to learn jpgraph and some of the font associations in the configuration have the case one way and they are stored on my system another. comic.ttf -> Comic.ttf. I tried 'lk comic.ttf Comic.ttf' and ended up with a comic.ttf file of the same size as the original Comic.ttf.

Now this is real lame but I do not know how else to put it. There are some links in the msttcorefonts which show up blue in my terminal. The one I tried to make is white.

Laughing is welcome as long as it is accompanied with an answer.

Searching the forums with symbolic, link and 'blue file' was an exercise in frustration.

Ed

In a terminal window, "ln -s original.file New.File" will create a symlink (symbolic link) from original.file, under the name New.File.

Lloyd B.

---

### Post by edpatterson on 2009-06-06
> **lloyd_b said:**
> In a terminal window, "ln -s original.file New.File" will create a symlink (symbolic link) from original.file, under the name New.File.

Lloyd B.

Thanks, If I could figure out how to mark the thread as solved I would.

Ed

---

### Post by snova on 2009-06-07
> **edpatterson said:**
> I tried 'lk comic.ttf Comic.ttf' and ended up with a comic.ttf file of the same size as the original Comic.ttf.

ln will create hard links by default. They are actually the same file- just accessible from two different paths.

> Now this is real lame but I do not know how else to put it. There are some links in the msttcorefonts which show up blue in my terminal. The one I tried to make is white.

As previously mentioned use the -s option to make ln create symbolic links.

---

