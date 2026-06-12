---
title: "error using boost library"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by premrajsv on 2010-06-30
Hello members,
I am working with tcp/ip program in rtnet. i am using boost library in c++ for realtime concept. while compiling a server program like,

./make_all.sh to make modules i am getting error like,

/usr/bin/ld: cannot find -lboost_system-gcc41-s
collect2: ld returned 1 Exit status
make:***[NetworkTest] Error 1

i ve installed boost library as well..can anyone help me with this issue...

---

### Post by jbo5112 on 2010-07-04
Try using -lboost_system instead of -lboost_system-gcc41-s

The names of boost's lib files in the packages don't include the compiler version.  I assume none of your work was done with gcc 4.1 anyway.  It hasn't been the default compiler version since Hardy (8.04) and the last release was on February 13, 2007.

---

