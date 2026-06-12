---
title: "compile error"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by deswal on 2011-04-14
I am  getting these errors when i compile sim_routing.cc program by this command
../../bin/cxx sim_routing.cc
g++ -Wall -o sim_routing sim_routing.cxx
following errors comes
../../common/priority_q.h : In member function 'bool guardedQueue<ITEM>::Validate(Const char*);
error : there are no argument to 'strcat' that depend on template parameter so a declaration of 'strcat' must be avaible.
error : <if you use -fpermissive  g++ will accept your code but allowing use of undeclared name is deprecated>
           when i tried to change in commom/priority_q.h file it shows it is read only file changes cannot be accepted.
how these errors can be removed.

---

