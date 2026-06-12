---
title: "error while installing qemu-kvm"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by nandakishore.ms on 2011-04-20
I am doing my m.tech researh project on cloud computing. I am beginner to ubuntu cloud. I am tryiing to install ubuntu cloud but i am facing the following problem.
 
I installed cc and nc already and nc is able to detect the cc and everything is working fine. Now i installed ubuntu desktop 10.10.
But while installing qemu-kvm the following error occured,
 
"package qemu-kvm is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. E: package qemu-kvm has no installation candidate."
 
can anyone help please, the problem need to be fixed as soon as possible. Please guide me with step by step procedure as i am very new to this environment.
 
thank u

---

### Post by falko on 2011-04-20
According to [http://packages.ubuntu.com/search?suite=maverick&section=all&arch=any&searchon=names&keywords=qemu-kvm](http://packages.ubuntu.com/search?suite=maverick&section=all&arch=any&searchon=names&keywords=qemu-kvm) , the package exists. Do you use the stock /etc/apt/sources.list, or did you modify it?

BTW, you can set up KVM as follows: [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10)

---

