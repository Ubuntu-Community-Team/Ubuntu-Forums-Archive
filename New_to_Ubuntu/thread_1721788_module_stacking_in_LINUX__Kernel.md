---
title: "module stacking in LINUX  Kernel"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by katochd46 on 2011-04-05
Hi, 
 
I am trying my hand with linux, just come across the concept of module stacking. It can be used to use symbol exported by other Modules. Means we can use something already made in some module so we do not have to redo something already done. But still i am not getting where in realtime we see this type of concept with linux. 
I am following following link same from o'reilly book. 
[http://www.makelinux.net/ldd3/chp-2-sect-5.shtml](http://www.makelinux.net/ldd3/chp-2-sect-5.shtml) 
 
>  
New modules can use symbols exported by your module, and you can stack new modules on top of other modules 
Stacking in the parallel port subsystem is shown in Figure 2-2; 

I am not able to understand this fig-2.2 :confused: 
 
> Using stacking to split modules into multiple layers can help reduce development time by simplifying each layer. 
Can you just give SOME EXAMPLE APLLICATION where we can use concept of module stacking it will increase my vision horizon :confused:
 
> For example, the video-for-linux set of drivers is split into a generic module that exports symbols used by lower-level device drivers for specific hardware. 
This book second chapter use to state about the module stacking. And also mentions about an example of **video-for-linux set of drivers**. As i have quoted above. So what i got is that generic viedio drivers can use any Specific Hardware dependent low level driver to do there work. Example like our web camera can be connected to Parallel port or USB port or Ethernet port. Upper level driver will remain same but lower level driver can be for USB, Parallel port or Ethernet & we can use some symbols exported by other modules to fullfill the requirement of lower level drivers. Am i right:confused:
 
greets, 
katoch

---

