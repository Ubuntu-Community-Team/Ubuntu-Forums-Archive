---
title: "Real quick dumb question- take one minute to answer"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by ddixonr on 2009-06-05
I don't know why I can't figure this one out. I have a game that I play (Urban Terror) and I usually use gnome-do to run it, but I came across a situation where I wanted to run it from the terminal. 

**How do execute ioUrbanTerror.i386 from the terminal?**

---

### Post by jonobr on 2009-06-06
typically to run anything that is not in your path you can either cd to the directory,

eg
```

cd ~/Destop/mygame/

```
and then execute
```

./<executablefile>

```

however, Im not sure about urban terror with the i386 extension

---

### Post by ddixonr on 2009-06-06
You got it! Thanks a ton.

---

### Post by jonobr on 2009-06-06
Cool

I thought it was a trick question :-)

---

### Post by daverave999 on 2009-06-07
I wrote myself a little script:
```
#!/bin/bash
/home/dave/UrbanTerror/ioUrbanTerror.i386
```

Saved it as /usr/bin/urt 
Did sudo chmod +x on it (make it executable). Can just type urt in at the terminal and it runs fine!

---

### Post by jonobr on 2009-06-07
hello


You could copy that file containing the start script you created to the desktop and then it would be just a double slick to start it , like a windows app. You would not need to open the reminal at all.
You can also  create your own icon for the file
Also, just to point out,
replace the dave with your own home directory name,.

---

### Post by unknownPoster on 2009-06-07
> **jonobr said:**
> 
replace the dave with your own home directory name,.

or better yet, (this should work on majority of modern Linux systems)

```
#!/bin/bash
~/UrbanTerror/ioUrbanTerror.i386 

```
"~/" is the "short-cut" to the home directory

---

