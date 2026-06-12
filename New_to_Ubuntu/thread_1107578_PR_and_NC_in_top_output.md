---
title: "PR and NC in top output"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-26
Hi,
When I examine the output of top, I can see many process with same NC have different PR. Doesn't nice value represent the priority? How those process differ in their PR? 
How to adjust PR in both C++ code and bash script?
Thanks!

---

### Post by lloyd_b on 2009-03-26
PR is a value calculated by the system, with NI being a major component of how it calculates it.

For more info (and for the various system calls you can use to change the priority of a process),[read this]("http://learnlinux.tsf.org.za/courses/build/internals/ch07s02.html")

Lloyd B.

---

