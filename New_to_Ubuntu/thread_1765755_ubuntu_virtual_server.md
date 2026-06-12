---
title: "ubuntu virtual server"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2011-05-23
Hi guys
I have setup a ubuntu 11.04 server

I want to install a ubuntu virtual server on it to host a web server, LAMP specifically. Ive read the ubuntu server guide but i seem to be missing something.

Can anyone recommend an alternative guide to setting up and managing a virtual server.
I dont have a great deal of experience with ubuntu server so the more basic the better.

Also any tips would be appreciated.

---

### Post by webofunni on 2011-05-23
which method u r planning to use. KVM or XEN ?

---

### Post by bigmonmulgrew on 2011-05-23
Im not set on either. Which would you recommend?

---

### Post by webofunni on 2011-05-23
KVM is the latest technology and it has built in support in kernel. You need to install XEN kernel for using XEN. 

But XEN support para virtualization and the overhead in that is very less compared to full virtualization in KVM. If you want full virtualization, you can go ahead with KVM. 

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

[http://en.wikipedia.org/wiki/Paravirtualization](http://en.wikipedia.org/wiki/Paravirtualization)

[http://en.wikipedia.org/wiki/Full_virtualization](http://en.wikipedia.org/wiki/Full_virtualization)

As per :

[http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine](http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine)

KVM also now supports para-virt. But I never used that. 

Also in XEN, your CPU need to support hardware virtualization to use full virtualization.

---

### Post by bigmonmulgrew on 2011-05-25
They are much more useful than the guide I was working on. They explain it a little more. and cover more. This makes it much easier to tailor it to my needs and fix issues.
The guide I tried first was  more "monkey see monkey do".
This keeps a guide short but leave you struggling if there are problems

Thanks a lot I now have a working vm which I can ssh to

---

### Post by webofunni on 2011-05-25
Good to hear that it helped :-)

---

