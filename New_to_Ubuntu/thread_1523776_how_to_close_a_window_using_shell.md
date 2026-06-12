---
title: "how to close a window using shell?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by sarosh on 2010-07-04
hi,
 suppose i have many windows open like two image files, a terminal , a firefox. and using command line i want to exit specifically 1 of these.. how can i do this?
 is there any shell command to do this?
 thanx...
 i am waiting for reply. its urgent!

---

### Post by spiky001 on 2010-07-04
if you type
```
top
```
it will give you running processes find the pid no then terminal

```
kill pid no
``` 

hope this is what you want

---

### Post by sarosh on 2010-07-04
thanx ...but it keeps on changing!:(
 any other way like

*_**close image2.jpg**_*or
[I][U][B]exit image2.jpg
[/B][/U][/I]
 i mean a command to do it?

---

### Post by spiky001 on 2010-07-04
the pid number stays the same if you press Q it will stop it then you can find the pid

---

### Post by spiky001 on 2010-07-04
if you want a gui system monitor will list the id of a process then you can kill it in terminal

try
```
ps -e
```

didn't know this just found it

---

### Post by nerdy_kid on 2010-07-04
```

killall PROGRAMNAME (i.e. firefox or eog)

```

---

### Post by sarosh on 2010-07-04
thanx all :)

---

