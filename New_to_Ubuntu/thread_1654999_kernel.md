---
title: "kernel"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-12-29
this is a theoretical question (as i am interested in understanding more about linux).
i've been seeing a lot about compiling new linux kernel.  why should you do it? why shouldn't you? and if possible - how it is done.
the more important question is - can i install (just like any other piece of software on linux) the new kernel (i compiled) onto the existing ubuntu (so to make it the ubuntu with the newest kernel?)

thanks

---

### Post by Wtower on 2010-12-29
Hi, please take a look first at: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by QLee on 2010-12-29
[QUOTE=daveboy23]this is a theoretical question (as i am interested in understanding more about linux).
i've been seeing a lot about compiling new linux kernel.  why should you do it? why shouldn't you? ...[/QUOTE]

In the old days it used to make sense because one could get some usable performance increase and save a bit of space. With modern hardware there is not the shortage of system resources as in the past. So, for the normal user you would see no benefit apart from the learning exercise, since with Ubuntu's short release cycle and fast upgrades one gets new kernels quickly and they are easy to install. The exception would be someone who needs some functionality not included with the Ubuntu kernel, but that isn't likely to be a beginner. The link given you by Wtower, could help if you choose to continue.

My recommendation, your time would be better spent leanring more about Ubuntu, than compiling your own kernel.


[Edit] I'll add, if you really want to learn GNU/Linux from the ground up, try Linux From Scratch, LFS. A search engine can easily find it for you.

---

### Post by daveboy23 on 2010-12-30
thank you so much for your reply

---

### Post by rvchari on 2010-12-30
hope you guys wont mind me joining in between... talking of kernel, i m using 10.10 and and 2.6.35-24 kernel. when i click on start > system > about ubuntu, it displays this in the start...

You are using Ubuntu 11.04
                - the Natty Narwhal - released in April 2011 and supported until October 2012.
	
can i know whats wrong ? everything is working fine, just this version clash !!!

---

### Post by matt_symes on 2010-12-30
Hi

> hope you guys wont mind me joining in between... talking of kernel, i m  using 10.10 and and 2.6.35-24 kernel. when i click on start > system  > about ubuntu, it displays this in the start...

You are using Ubuntu 11.04
                - the Natty Narwhal - released in April 2011 and supported until October 2012.
	
can i know whats wrong ? everything is working fine, just this version clash !!!

Off topic. You should have started a new thread. However, to answer you, this is a known bug.

Kind regards

---

### Post by Paqman on 2010-12-30
> **QLee said:**
> 
My recommendation, your time would be better spent leanring more about Ubuntu, than compiling your own kernel.


+1

Very, very few people will have a solid practical reason to do it, most people who try are just tinkering around. Tbh, there's a lot of complicated options involved, and if you don't know what you're doing you're just as likely to end up with a kernel that is less well optimised for your system than the generic one that Ubuntu offers.

---

