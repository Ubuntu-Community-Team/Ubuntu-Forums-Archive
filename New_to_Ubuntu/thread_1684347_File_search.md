---
title: "File search"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Steve Moss on 2011-02-09
How can I search all directories?

It seems I have to choose a specific search (eg home) but I don't know where the file is that I am looking for

What I want to do is a Windows style search that finds it anywhere on my computer

Thanks in advance for any advice :)

---

### Post by taseedorf on 2011-02-09
try searching synaptic for gnome panel file search

also search / and that should search entire drive

---

### Post by Primefalcon on 2011-02-09
go to places->search for files

---

### Post by oldos2er on 2011-02-09
If you know the name of the file you're searching for, from your home folder run ```
find . -name foo
``` To search all folders from the root folder, ```
 cd /
sudo find . -name foo
```

---

### Post by matt_symes on 2011-02-09
Hi

From the terminal you can also use

```
locate <filename>
```

to locate a file quickly by using indexes. However the indexes need to be updated for recently added files. 

```
sudo updatedb
```

Cron calls this once a day i believe (or anacron kicks in). Good for finding files that have been indexed but find is better (but slower) for finding files that have been very recently added to the file system before the last call to updatedb. I.E in the last day.

So in summary, find should always find the file but it is slower. locate will only find the file if it has been added to the index database and that happens once a day but locate is very quick.

Kind regards

---

### Post by Steve Moss on 2011-02-11
Thansk for all the helpful advice

---

