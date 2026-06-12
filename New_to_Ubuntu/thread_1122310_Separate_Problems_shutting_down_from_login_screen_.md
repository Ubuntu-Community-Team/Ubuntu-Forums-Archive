---
title: "Separate Problems shutting down from login screen and desktop"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by superdan006 on 2009-04-10
Hello everyone,

I am running Ubuntu 8.10 Intrepid Ibex on a Intel(R) Pentium(R) 4 CPU 2.80GHz on a Compaq Presario. I'm not entirely sure what other information I need to provide. Here are the two problems I am having:

1) When I try to shutdown from the Ubuntu login prompt, the Ubuntu meter powers down, some script is shown, and when the machine tries to halt, The following script is shown:
halt: Unable to iterate IDE Devices: No such file or directory.

2) When I try to shutdown from the Ubuntu desktop after logging in, the Ubuntu meter powers down but then no script appears at all after and all that is displayed is a flashing underscore.

Each of these problems is solved when I manually power off the machine, but I do not know what kind of effect this has on the computer and would thus prefer not to do this. 

I tried to solve these problems independently and through searching on google. 
Problem 1) was solved (I think) when I added apm power_off=1 to the /etc/modules file. Ubuntu will power down and then the computer will shut off. I don't see any scripts. Thanks to everyone who posted this solution online.
Problem 2) is difficult to properly explain so I didn't bother searching for it. 

Now, I understand these problems may constitute a reportable bug. What is the procedure for reporting one again?

Thanks for your time,
-Dan

---

### Post by Didius Falco on 2009-04-11
Hi Dan,

Here is a link to the bug reporting procedure:

[http://www.ubuntu.com/community/reportproblem](http://www.ubuntu.com/community/reportproblem)

I hope they can fix it for you...

---

### Post by superdan006 on 2009-04-11
Thanks Didius

---

