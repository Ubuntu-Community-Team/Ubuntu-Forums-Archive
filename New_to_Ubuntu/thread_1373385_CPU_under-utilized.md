---
title: "CPU under-utilized"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Ron O on 2010-01-05
Running an older Intel dual core 2.8 processor in Xubuntu, I notice that the CPU seems to be underutilized, as seen in System Monitor, when compared to CPU utilization when running Windows. 

For example, if I run a processor intensive task (like calculating prime numbers-as a test) in Windows, each core automatically runs at or near 100%. If I do the same task in XUbuntu Jaunty, one core runs at 100% while the other one is nearly idle.

Is there a way to get Jaunty to fully utilize the CPU like it does in Windows IN GENERAL (not process specific)? What's the point of having a dual core CPU when it runs like a single core when under peak demand?

---

### Post by Cheesemill on 2010-01-05
This all depends on the application, if an app isn't written to be multi-threaded then it can only ever use one core.

Your Windows prime number application is multi-threaded but the Ubuntu one isn't.

This is always going to be process specific depending on the application, the majority of Windows apps will only ever use one core.

---

### Post by Sir Jasper on 2010-01-05
Hi,

I have dual boot of W98SE and Xubuntu and I would be most interested to know which prime number program you are running and which was the particular test you carried out (assuming it is a free linux program) and also how long it took.

I will then attempt an identical test on my somewhat ancient machine with the intention of posting my results here, if that would be of interest to you.

My regards

I use three well known, lightning fast, prime number programs for windows
and, if appropriate, I would also be happy to post comparative results for any of those as well.

---

### Post by Bartender on 2010-01-05
I think Cheesemill hit the nail on the head.  Handbrake for Linux utilizes both cores on our Core2Duo lappy.

---

