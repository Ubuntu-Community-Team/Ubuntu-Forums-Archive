---
title: "Can I run Ubuntu from a Physical Partition on Virtualbox?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by looi76 on 2009-04-29
On my computer I have both Ubuntu Intrepid and Ubuntu Jaunty - both of them are 64bit versions. Is it possible to run Ubuntu Intrepid using Virtualbox on Ubuntu Jaunty?

---

### Post by cariboo on 2009-04-30
You should be able to run any operating system in a vm, I currently have Xp Pro, Vista, Windows 7 and freenas vm's

---

### Post by anewguy on 2009-04-30
Your title mentions "from a physical partition".  If you mean can you run virtualbox in 1 OS using a physical disk instead of a virtual disk, the answer is yes, you can, but it usually hasn't been recommended.  However, most of those questions have revolved around running Windows from a physical disk in a VB virtual machine in Ubuntu - and that can cause some problems (it works - I've done it, but I wouldn't recommend it).  However, running 2 versions of Linux from physical devices shouldn't be a problem I wouldn't think.  Back when I tried all of this you had to set it up in definition file for your virtual machine, but this was done easily using vboxmanage - there used to be an advanced section in the help that comes with virtualbox that told how to do this.

Good luck!

Dave :)

---

