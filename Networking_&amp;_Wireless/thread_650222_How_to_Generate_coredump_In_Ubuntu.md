---
title: "How to Generate coredump In Ubuntu ?"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by amaresh_83 on 2007-12-26
Hi Friend,

              see one simple programme which will creat core Dump. 
           <filename>==core.c
           #include<stdio.h>
           int 
           main() {
                       int i = 10 ,j =0;
                       printf("value is %d",(i/j));
            }
            after compiling getting message as floating point core dump.
            But i'm not getting that core image like as core.1235 in ubunt.
       So can anybody will guide me .
 I know how to creat core file as ulimit -u -c 1000000 in /etc/profile

but in Ubuntu i'm confuse so please help me out.

---

