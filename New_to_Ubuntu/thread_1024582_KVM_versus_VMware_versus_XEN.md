---
title: "KVM versus VMware versus XEN"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-29
I have been using VMware 1.06 to virtualize an XP instance on my Ubuntu 8.04 PC.  This weekend I picked up the "Dummies guide to Virtualization" and learned that my CPU will support KVM - Kernel Virtual Machine.  

So, what are your perceptions and experiences with KVM?  How does it compare to VMware and XEN?

Carl

---

### Post by blueridgedog on 2008-12-29
My perception was that VMware was more robust and further along the development path.

---

### Post by wmoore on 2008-12-29
Be aware than Xen uses a very different kind of virtualisation than VMware, and you would need to install a completely new kernel to use it. I would stick with VMware to be honest, or possibly give Virtualbox a try.

---

### Post by cwmoser on 2008-12-29
Regarding the Virtual Machines, is there any compatibility between VMware, Virtual Box, KVM, etc.

Carl

---

### Post by cwmoser on 2008-12-29
Regarding VMware, I use v1.06 because I had difficulty getting 1.08 to work.  I did install 2.0 but I thought the web interface was kinda clunky.

Comments?

Carl

---

### Post by mattman85 on 2008-12-29
> **cwmoser said:**
> Regarding the Virtual Machines, is there any compatibility between VMware, Virtual Box, KVM, etc.

Carl

As far as between VMWare and Vbox, I've heard tell of vdi's being somewhat compatible.  i'm not sure, though.  It's never been successful for me.

I use VBox on my systems.  

Tangent...
my parents XP desktop (gateway E-4500D) has virtual Fedora 10.

my work laptop (OS X Leopard Macbook Pro) has virtual: XP, Ubuntu 8.10, [gOS Gadgets 3]("http://thinkgos.com/") (just to see what gOS was like - it's not google OS, but rather good OS), and MS DOS 6 (just because I miss DOS that much).  

my personal laptop (gateway mx6448 64-bit) dual boots XP and Ubuntu 8.04, with virtual Backtrack 2 and Backtrack 3 beta for computer forensics work.

back on track, I think..

with both VMWare (free version) and VBox on the Mac, I had to do a little tweaking to get the virtual xp to see the network, but aside from that, I haven't run into any issues. 

The free VMWare works just as well as VBox on any system, but I chose VBox because I like to show my support to the open source world.

---

