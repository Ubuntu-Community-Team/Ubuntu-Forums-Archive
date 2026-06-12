---
title: "Can't install updates/packages."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Mazza558 on 2009-01-05
When trying to run update manager, it opens briefly and then closes. Running it in the terminal comes up with "Bus Error". The same goes for trying to install individual packages. 

Help!

---

### Post by oldos2er on 2009-01-05
Can you copy and paste the full error here?

---

### Post by halitech on 2009-01-05
can you open a terminal and run ```
sudo apt-get update
```and post back any messages it gives. This will help us determine the issues better.

---

### Post by Mazza558 on 2009-01-05
All I get when running those is "Bus error" - nothing else.

---

### Post by halitech on 2009-01-06
according to this: [http://en.wikipedia.org/wiki/Bus_error](http://en.wikipedia.org/wiki/Bus_error) a bus error is the result of the CPU not being able to access memory physically. do you have the live cd? if you do, boot into it and run the memtest for a few hours and see if you have some bad ram

---

