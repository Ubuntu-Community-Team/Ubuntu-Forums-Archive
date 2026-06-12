---
title: "How do I limit the output of the ls command to show me one page then prompt for more?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Captain_Glen on 2009-11-17
How do I limit the output of the ls command to show me one page of results.  Then I want it to wait till I press a key before going on to the next page.

I am sure I have seen this done but I can't find the option in the man pages.

---

### Post by skatinjj on 2009-11-17
ls | more

press enter to advance one line

press space to advace a page

---

### Post by dillandriskell on 2009-11-17
```
ls | less
```

---

### Post by ctyc on 2009-11-17
Uhm you pipe it through the more comand

ls|more


Good Luck

---

### Post by Captain_Glen on 2009-11-17
Cool thanks!

---

### Post by phrostbyte on 2009-11-17
ls | less

lets you go in reverse too

less is a pun on "less is more" etc.

you can also use it to view files

eg: 

less somefile.txt

---

### Post by Old *ix Geek on 2009-11-17
I prefer **pg**:

ls -l | pg

To see its usage/options:

man pg

---

### Post by blazemore on 2009-11-17
+1 for less

---

### Post by Hilko on 2013-01-09
To see the last 10 most recently changed files
```
ls -ltr | tail -n 10 
```

---

### Post by sisco311 on 2013-01-09
Old thread closed.


[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

---

