---
title: "running g++ in shell"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by manish411 on 2010-07-31
i installed gcc compiler . I now created a folder in which I keep all the source codes.
after compiling my program I get an icon a.out.
what is this

---

### Post by lisati on 2010-07-31
a.out is the output from gcc: it's your executable file.

---

### Post by manish411 on 2010-07-31
but after compiling more than 2 source files i still get only 1 icon.
whose executable file is this

---

### Post by da burger on 2010-07-31
If you compile two source files at the same time they get "linked" into one executable. You can do this intentionally when you want to put different functions in different files or in you case by accident. If you didn't want these to end up as one executable run g++ twice (once on each file).

---

