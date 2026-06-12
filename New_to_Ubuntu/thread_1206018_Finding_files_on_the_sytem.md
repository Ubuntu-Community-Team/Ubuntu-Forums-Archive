---
title: "Finding files on the sytem"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by OllieGab on 2009-07-06
I seem to fail in the most simple tasks at the moment!!

What is the easiest way of finding a file that I may know only part of the file name of. Similar to windows where you just put an * to cover part of the name.
I've tried the desktop search function but it never seems to return anything I'm looking for. And I'm not quite sure of what the Tracker does...it just says 'idle' most of the time!

Ollie

---

### Post by CLomax on 2009-07-06
There's a search applet you can add to the panel. Right click on the panel and click *Add to Panel...*, it's there somewhere.

---

### Post by OllieGab on 2009-07-06
There is a search tool there but though I added it to the toolbar it gives the error message: "Could not launch......Failed to execute child process "gnome-search-tool" (No such file or directory)"

I have it installed but there must be something missing??!!

---

### Post by Celauran on 2009-07-06
> **OllieGab said:**
> 
What is the easiest way of finding a file that I may know only part of the file name of.

```
find / -name *whatever*
```

If you have an idea where in the directory tree it is, you can narrow down further (ie. replace / with /home)

---

### Post by jonobr on 2009-07-06
hello


if you are looking for a file named myfile.txt and its located somewhere in or below your home directory, then just open a terminal window 
and type

find . -name myfile.txt
or  more generally using wildcard

find . -name myfile*
or 
find . -name *.txt

This will seach in the home directory.

If you wanted to search in a specific directory you could use

find ~/Desktop/myfolder/mytextdocs/ -name my*

The . or dot means , find from the current directory

the tilda or ~ means find from the current directory

---

### Post by CatKiller on 2009-07-06
locate -i string

---

