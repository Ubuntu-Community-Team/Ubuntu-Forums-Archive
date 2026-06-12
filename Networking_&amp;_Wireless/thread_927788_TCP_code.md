---
title: "TCP code"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by stion on 2008-09-23
Hello i was wondering if anybody know where to get a tutorial for the current running TCP code that is used in Ubuntu 8.0. I was looking for something that would specify what the sections of code would do and how the parameters of code effect the overall operation of TCP. Also if possible how it would differ from the TCP running in Windows 2000

Thanks in advanced any information is greatly appreciated.

---

### Post by fwre01 on 2008-09-23
thats a good question, is there an IP stack version? and if so, what version is ubuntu 8.04 or 8.10 running?

...i know i havent answered the question here, but at least it will bump it :)

---

### Post by shanix on 2008-09-23
command:

/sbin/sysctl -a | grep net

Should give you more information regarding TCP/IP on your system.

---

### Post by stion on 2008-09-23
> **shanix said:**
> command:

/sbin/sysctl -a | grep net

Should give you more information regarding TCP/IP on your system.


Thank you that did help quite a bit the only thing is that that command outputs so much data that i am unable to scroll all the way to the top is there any way to fix this ??

Also how do you check the exact version of the dirsto that you are running ??

Thanks again.

---

### Post by shanix on 2008-09-23
Find out version:

 lsb_release -a

View the message page by page:

<command> | less

ex:


/sbin/sysctl -a | grep net | less

---

### Post by stion on 2008-09-23
Awesome thanks for the information 

I am currently running Ubuntu 8.04.1 

Is debian TCP the same as Ubuntu TCP i know that there are slight variation in how each implementation generates the ISN and the Port numbers and thats not to important to me.. it more the overall code and how it works.

---

