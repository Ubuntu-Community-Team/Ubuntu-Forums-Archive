---
title: "household ubuntu, configuration, kernels, nvidia and compiz"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by dookiebowser on 2010-06-11
I've been trying to compile my first kernel and it got me thinking. Are there kernel sources out there that are pre-configured towards specific manufacturers? Or even kernels that are specifically designed for the average home user? There is a lot of hardware in the kernel configs I've never heard of,  and some I have....10-15 years ago.

Ubuntu is awesome at hardware detection and the drivers haven't really given me any problem, but I can only assume this is because it is equipped for nearly anything users throw at it. Including ancient or rare hardware. 

I think I should have started by asking -- does Ubuntu and it's variants  decide what is necessary for your hardware to run properly and install  those drivers and modules, or does it install everything and decide what  to use after it's installed? For instance, I have an HP laptop and don't need Dell specific modules. Do they come built into the kernel or even as a module if I'm not using a Dell?

Is there anything out there between *compiling your own kernel* and a *one size fits all *distro? Does the alternate ubuntu install have what I'm looking for in terms of  configuration?

I was trying to enable compiz through System->Appearance. It wouldn't allow me to enable it with Nouveau, or with any of the closed Nvidia drivers through Administration->Hardware Drivers including the "current" drivers. I downloaded the latest drivers for linux off of the nVidia site and was able to install them and had no problem with compiz afterwards. Is the nvidia driver in the repositories really the current driver? 

I forgot to add when trying to enable Compiz at the beginning and the current drivers enabled through Administration->Hardware Drivers, it kept trying to download the current drivers (and failing because it would hang) even though they were already current (or so me and Ubuntu thought)?


Thanks a lot in advance. ):P

---

### Post by bodhi.zazen on 2010-06-11
Most distros use a generic kernel with as you noticed a large number of modules. This is ideal for hardware detection and unlikely to change any time soon.

There are some variations, ie server or pae kernels for example, but from there you would need to compile your own, only you know your hardware and what you can remove.

With that in mind, with anything resembling modern hardware I have not found compiling a custom kernel makes much difference in performance. Most desktop applications, firefox, openoffice, etc run about the same.

There are a few merits for running a custom kernel from a security perspective, a custom kernel with minimal modules is more secure then the gen kernel.

It depends on how much you wish to learn about the kernel and how much time you wish to spend on it.

---

### Post by dookiebowser on 2010-06-11
> **bodhi.zazen said:**
> There are a few merits for running a custom kernel from a security perspective, a custom kernel with minimal modules is more secure then the gen kernel.

It depends on how much you wish to learn about the kernel and how much time you wish to spend on it.

Thanks a lot for that info. I don't mind putting the time in and getting my computer set up specifically for what I need it for and then imaging the drive.

I was just imagining that setting up would be better if say, the desktop version of Ubuntu asked you for your specs and installed accordingly. Windows has made me a minimalist.

Thanks again.

---

### Post by bodhi.zazen on 2010-06-11
> **dookiebowser said:**
> Thanks a lot for that info. I don't mind putting the time in and getting my computer set up specifically for what I need it for and then imaging the drive.

I was just imagining that setting up would be better if say, the desktop version of Ubuntu asked you for your specs and installed accordingly. Windows has made me a minimalist.

Thanks again.

Well, if you really want to do it right, you should consider Gentoo. Gentoo allows you to easily do these types of customizations from kernel up to every application you compile.

---

### Post by dookiebowser on 2010-06-11
> **bodhi.zazen said:**
> Well, if you really want to do it right, you should consider Gentoo. Gentoo allows you to easily do these types of customizations from kernel up to every application you compile.

This seems right up my alley. 

I tried to install debian when I was a kid and failed miserably, there were too many things relating to hardware in the installation I didn't understand. This has made me pretty terrified of installing anything not point and click since then but it's been a loooong time and I have a loooot more knowledge now.

I've heard a lot of good things about Gentoo. Am I to understand that Gentoo can come as FreeBSD or Linux? If so, which would be better for home use and Mono for C#? I'm ignorant but I always think of a server when I hear BSD, would this be accurate?

Thanks again for following up! :-D

*Also, I forgot to ask. What is the difference between unloading a module and never installing it as a module in the first place?

---

### Post by bodhi.zazen on 2010-06-11
Gentoo is a version of Linux. I am guessing you are thinking of the portage system, which is a terminology shared with gentoo and freebsd.

[http://en.wikipedia.org/wiki/Portage_%28software%29](http://en.wikipedia.org/wiki/Portage_%28software%29)

See also :

[http://www.gentoo.org/](http://www.gentoo.org/)

You will need to read the documentation

[http://www.gentoo.org/doc/en/?catid=install](http://www.gentoo.org/doc/en/?catid=install)

Gentoo allows you to tweak your system as much or as little as possible.

I think the best way to understand how to compile a kernel is to compile a kernel, lol

Basically (over simplification) when compiling a module you either build it into the kernel or build it as an optional module to be loaded as needed.

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40)

---

### Post by dookiebowser on 2010-06-11
> **bodhi.zazen said:**
> Gentoo is a version of Linux. I am guessing you are thinking of the portage system, which is a terminology shared with gentoo and freebsd.

[http://en.wikipedia.org/wiki/Portage_%28software%29](http://en.wikipedia.org/wiki/Portage_%28software%29)

See also :

[http://www.gentoo.org/](http://www.gentoo.org/)

You will need to read the documentation

[http://www.gentoo.org/doc/en/?catid=install](http://www.gentoo.org/doc/en/?catid=install)

Gentoo allows you to tweak your system as much or as little as possible.

I think the best way to understand how to compile a kernel is to compile a kernel, lol

Basically (over simplification) when compiling a module you either build it into the kernel or build it as an optional module to be loaded as needed.

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40)

As per the Gentoo site: 
> What is Gentoo?
  Gentoo is a free operating system based on either Linux or FreeBSD 


That's why I was confused.

So if I compile the kernel with modules built-in, they cannot be removed? If it's installed alongside the kernel as a module, and I unload it at a later time -- is it any different than never installing it at all? Does that mean it would only reside on the disk with no other interaction?

I've already started on the installation documentation. I'm not afraid to read but always appreciate the cliffs notes!! :)

Thanks again.

---

### Post by bodhi.zazen on 2010-06-11
> **dookiebowser said:**
> As per the Gentoo site: 



That's why I was confused.

So if I compile the kernel with modules built-in, they cannot be removed? If it's installed alongside the kernel as a module, and I unload it at a later time -- is it any different than never installing it at all? Does that mean it would only reside on the disk with no other interaction?

I've already started on the installation documentation. I'm not afraid to read but always appreciate the cliffs notes!! :)

Thanks again.

I think you get the general idea yes. I ran gentoo several years ago and honestly do not know what to tell you re: Gentoo BSD.

[http://www.gentoo.org/proj/en/gentoo-alt/bsd/](http://www.gentoo.org/proj/en/gentoo-alt/bsd/)

---

### Post by sandyd on 2010-06-11
> **dookiebowser said:**
> As per the Gentoo site: 



That's why I was confused.

So if I compile the kernel with modules built-in, they cannot be removed? 
If it's installed alongside the kernel as a module, and I unload it at a later time -- is it any different than never installing it at all? Does that mean it would only reside on the disk with no other interaction?
**If you compile it as a module, the module is loaded "as needed" meaning that it will not load if no hardware on your system needs it. Typically, the best thing to do is to identify the drivers your hardware needs, then compile those as built in modules. Leave the rest as modules. This will optimize your boottime and efficiency ;)**

I've already started on the installation documentation. I'm not afraid to read but always appreciate the cliffs notes!! :)

Thanks again.
.

---

### Post by bodhi.zazen on 2010-06-11
For anyone interested in gentoo/BSD reading this thread :

[http://www.gentoo.org/doc/en/gentoo-freebsd.xml](http://www.gentoo.org/doc/en/gentoo-freebsd.xml)

---

### Post by dookiebowser on 2010-06-11
> **bodhi.zazen said:**
> For anyone interested in gentoo/BSD reading this thread :

[http://www.gentoo.org/doc/en/gentoo-freebsd.xml](http://www.gentoo.org/doc/en/gentoo-freebsd.xml)


I knew you were going to investigate it! hah! I think I'll go with Gentoo linux as I've never used BSD and am already making a venture. Thanks a lot for your help and knowledge!

@carlee thanks a lot for your input but with every answer it raises 5 other questions to me :)

---

