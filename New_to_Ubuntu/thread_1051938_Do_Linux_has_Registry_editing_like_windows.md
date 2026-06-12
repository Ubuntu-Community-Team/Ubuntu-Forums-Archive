---
title: "Do Linux has Registry editing like windows"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by halovivek on 2009-01-27
Hi
I am having one doubt. I have not tried yet to this. In windows we do some registry edit for pop-ups and to block some problems.
In Linux ( in gnome, KDE and all other desktop variants) Do we have the Registry edit something like that?
If so can you provide me the link to read more?

---

### Post by hyper_ch on 2009-01-27
no, everything is configured in different text files.

---

### Post by TheLions on 2009-01-27
gnome has registry!
but it is tiny one!

type gconf-editor in terminal

---

### Post by sydbat on 2009-01-27
> **TheLions said:**
> gnome has registry!
but it is tiny one!Um...no...> Windows has the Registry to keep track of settings. Linux, in contrast, has dotfiles (files whose names begin with a period). While GConf and the Windows Registry share the same goal, it is important to note that the similarities end there.Reference - [http://arstechnica.com/software/reviews/2003/09/gnome2-4.ars/4](http://arstechnica.com/software/reviews/2003/09/gnome2-4.ars/4)

---

### Post by halovivek on 2009-01-28
> **hyper_ch said:**
> no, everything is configured in different text files.

So what is the major difference between configuring as files (in linux) and in registry (in windows). I need more explanation. I am creating a document and planning to post the difference between windows and Linux in a different way.

---

### Post by snova on 2009-01-28
> **halovivek said:**
> So what is the major difference between configuring as files (in linux) and in registry (in windows). I need more explanation. I am creating a document and planning to post the difference between windows and Linux in a different way.

Linux programs typically keep their own configuration files, often in hidden folders in your home directory. This is in contrast to the Windows registry, in which programs stash their stuff in an central operating system-provided "hive".

There are a few libraries around to provide a service like Windows' registry; KDE and Gnome have one, for example.

---

