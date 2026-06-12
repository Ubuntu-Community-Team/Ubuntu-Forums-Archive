---
title: "Remove all folders called Originals in Photo Collection"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Daniel591992 on 2009-04-18
Hey,

I'd like to get rid of every folder called Originals in my photo collection. How would I do this using the command line?

Thanks

---

### Post by roquefilipe on 2009-04-19
Explore the find command, try something like this:

```
find /home/ -name *originals* -type d
```

-type d means it is a directory

I recommend that you use a two step process. First identify what files and folders you want to remove. Then just remove them. It is possible to use the find command to delete the files, but a mistake may be fatal for your data.

---

### Post by Daniel591992 on 2009-04-19
> **roquefilipe said:**
> Explore the find command, try something like this:

```
find /home/ -name *originals* -type d
```

-type d means it is a directory

I recommend that you use a two step process. First identify what files and folders you want to remove. Then just remove them. It is possible to use the find command to delete the files, but a mistake may be fatal for your data.

Hi, I did that and it listed the ones I want to delete. How would I actually delete them though. Thanks

---

### Post by huxain1981 on 2009-04-19
try this link 
[http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

i haven't tried it, so let me know if it works :D

---

### Post by Daniel591992 on 2009-04-19
> **huxain1981 said:**
> try this link 
[http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

i haven't tried it, so let me know if it works :D

Hi, I still couldn't find one for folders. Anyone else know?

---

### Post by huxain1981 on 2009-04-21
> **Daniel591992 said:**
> Hi, I still couldn't find one for folders. Anyone else know?


   ```
find . -name "FILE-TO-FIND" -exec rm -rf {} \;
```

this command worked for me.

---

### Post by bladeswords on 2009-04-21
You could just combine the example provided above with the one from the website and it should come out to be...

```
find /home/ -name *originals* -type d -exec rm -rf {} \;
```

---

### Post by andrew.46 on 2009-04-23
Hi bladeswords,

> **bladeswords said:**
> You could just combine the example provided above with the one from the website and it should come out to be...

```
find /home/ -name *originals* -type d -exec rm -rf {} \;
```

A slightly more cautious approach would be:

```
find $HOME -name 'Originals' -type d -ok rm -rf {} \;
```

Bearing in mind that there is almost no way to recover files and directories deleted by such a command. In particular the '-r' options means 'recursive' and thus will delete *all* files and *all* subdirectories and all of *their* contents below the level of the directory that has been found. ***[COLOR="Red"]So be very sure this is what you want to do!![/COLOR]***

Andrew

---

