---
title: "new begginer &amp; starter"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by zungeru on 2010-12-28
Dear all,
I am a new beginner of Ubuntu, presently researching, & have to use ubuntu for my network simulation using NS2 & C++, I tried this set of codes as a new beginner, but errors could allow me to move forward. here are the codes & the errors underneath.
Please help.



nf [open out.nam w] 
  $ns namtrace-all $nf 
   
  proc finish {} { 
  global ns nf 
  $ns flush-trace 
  close $nf 
  exec nam out.nam & 
  exit 0 
  } 
  set n0 [$ns node] 
  set n1 [$ns node] 
   
  $ns duplex-link $n0 $n1 1Mb 10ms DropTail 
   
  $ns at 5.0 "finish" 
   
  $ns run 
   
   
  zungeru@zungeru-AOA110:~$ ns example1.tcl 
  can't read "ns": no such variable 
      while executing 
  "$ns namtrace-all $nf" 
      (file "example1.tcl" line 2) 
  zungeru@zungeru-AOA110:~$

---

