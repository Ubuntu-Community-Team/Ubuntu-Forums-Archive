---
title: "Server installation"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Lorenz_NZ on 2009-05-16
Hi, I'm familiar with the Windows server and workstation environments but totally new to Linux...

I have a few windows computers connected via wireless, one via cable and a Supermicro server.

What I want to achieve is to build an Ubuntu server:
1. to learn Linux operating system and administration
2. to build different virtual servers on the supermicro (testing purposes only - no business)
3. to build different virtual desktops - for testing different operating systems and software

Idea is to have several images to play with - if one break I can delete it and build a new VM

I have both Ubuntu server and desktop versions

I have installed the server version and it starts up fine.
Where do I start with the configuring of the server?
How do I access it from the windows PCs - is eBox be the best to use?

---

### Post by Didius Falco on 2009-05-16
> **Lorenz_NZ said:**
> Hi, I'm familiar with the Windows server and workstation environments but totally new to Linux...

I have a few windows computers connected via wireless, one via cable and a Supermicro server.

What I want to achieve is to build an Ubuntu server:
1. to learn Linux operating system and administration
2. to build different virtual servers on the supermicro (testing purposes only - no business)
3. to build different virtual desktops - for testing different operating systems and software

Idea is to have several images to play with - if one break I can delete it and build a new VM

I have both Ubuntu server and desktop versions

I have installed the server version and it starts up fine.
Where do I start with the configuring of the server?
How do I access it from the windows PCs - is eBox be the best to use?

Hi, and welcome to the Ubuntu forums!

I can't answer a single question you have - I've never installed or run the server version.

What I can do is point you to some documentation that should help you getting started:

[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

I hope this helps...

Regards,

Didius

---

### Post by Paul41 on 2009-05-16
I run a linux server at my house but have never done it in a VM so I won't be any help there. As far as the best way to access it from a Windows machine use PuTTY to access it with ssh. [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by Crandom on 2009-05-16
If you're looking to go into sysadmin'ing a linux system for buisness, it will almost definately going to be Red Hat (like red hat, fedora) rather than Debian based like Ubuntu. If you're ding this solely for that reason, Red Hat is for you. (CentOS is the free version).

Otherwise, other people can help you here.

---

### Post by Lorenz_NZ on 2009-05-16
Thanks for your suggestions - I'll download putty and see how that part go.

The idea is to get to the system admin in the end but at the moment Linux is totally new. I found the desktop version of Ubuntu very easy to install and it is detecting all the hardware correctly without problems.

I have not tried CentOS yet; but some linux versions is not working on the Supermicro hardware - I started with VMWare then Solaris with no avail.

---

