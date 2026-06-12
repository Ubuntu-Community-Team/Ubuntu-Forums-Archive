---
title: "Beginner - Listing only n results with ls"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by RakeshSugirtharaj on 2009-12-10
Hi,

I am a beginner to linux and ubuntu. Can anyone pls tell me how to list only 'n' results when i do 'ls' command? I couldnt find anything related in the man pages of ls.

---

### Post by NT4usB on 2009-12-10
No idea how to limit the results to 'n' but you can limit the results to the screen by piping ls to less:```
ls | less
```Arrow or Page up/down to navigate through the results.
```
q
``` to exit.

---

### Post by RedSingularity on 2009-12-10
If you are looking for things with n in it try this........

ls | grep n*

---

### Post by NT4usB on 2009-12-11
doh... I thought the OP was looking for n(umber) of results, like show only 15 lines or something...

---

### Post by ukripper on 2009-12-11
in current directory ```
ls -al n*
```

---

### Post by ukripper on 2009-12-11
> **NT4usB said:**
> doh... I thought the OP was looking for n(umber) of results, like show only 15 lines or something...

you could be right, but post is bit confusing.

---

### Post by diesch on 2009-12-11
```
ls | head -n2
```

---

### Post by ukripper on 2009-12-11
i normally use ```
tail -n 10 /directory/files
```

for files

---

