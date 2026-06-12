---
title: "Loop jamming"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by newport_j on 2010-03-01
I would like to know if the gcc complier can do loop jamming with a command line option? I am pretty sure that gcc can do loop unfolding, the the next step would be loop jamming. I read online at the HP website about loop jamming and it seems to be something that I may  find useful in my work. 

Newport_j

---

### Post by avidday on 2010-03-01
The vectorization optimizations you have already been told about in gcc4 can do limiting loop fusion/jamming. You can refresh your memory [here]("http://gcc.gnu.org/projects/tree-ssa/vectorization.html"). 

Loop jamming/fusion isn't a magic bullet, though. Often it can be slower than using separate loops because of worsened cache coherence.

You will do much better by hand vectorizing critical sections of code using SSE/SSE2 intrinsics than trying to coax the compiler to do it for you. But that requires accurate profiling and an understanding of the code you are working with, which is probably not something within your grasp at present.

---

