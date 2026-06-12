---
title: "Terminal question"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by topic58 on 2008-12-25
A simple question here about the terminal. I want to list a long list of names, let's say from A to Z. But the terminal just shows K to Z. How to see A to K?? This is driving me crazy. I understand there are too many files to be shown/ listed in one terminal window. But there must be a simple way to see the first of my long long list of files..

---

### Post by taurus on 2008-12-25
```
more filename
```
It will show you the first 24 lines in filename.  Then, hit the space bar for the next 24 lines...

---

### Post by Marshal0505 on 2008-12-25
just pipe it with a reader like 'less' or 'more'
So a command like 

```
locate -i blahblah
```

is handled by less like so 

```
 locate -i blahblah | less
```

this makes the output controlable with the spacebar.

Alternatively you could direct the output to a text file.

---

### Post by Mega-G33k on 2008-12-25
You could try 

```
ls /dev | more
```

replace /dev with the directory you want to list

---

### Post by jerome1232 on 2008-12-25
also you can just scroll up using shift+pgup/pgdown, this works in tty's too.

---

### Post by topic58 on 2008-12-25
Thanks a lot. I got it done by doing this:

from my directory I wrote: ls | more

then I had to scroll enter window by window.

---

