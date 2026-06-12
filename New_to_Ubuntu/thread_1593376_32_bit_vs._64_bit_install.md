---
title: "32 bit vs. 64 bit install"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-10-11
I guess my question is: what's the difference? I am currently running Ubuntu 10.10 (Maverick) and it is 32 bit. Everything works great. However, I have a BRAND NEW computer that came with 64 bit Windows 7 installed. Should I have installed the 64 bit version? Why or why not?

Thanks!

---

### Post by juil on 2010-10-11
I haven't done much research into the differences but here's a quote i came across in one of the Ubuntu-Linux website in google:

> In my opinion, there’s no need to use this,  even  if  you  have  a  64&#8208;bit&#8208;capable  CPU  in  your  computer, unless  your  computer  has  more  than  4GB  of  RAM.  The  64&#8208;bit version  of  Ubuntu  has  been  known  to  present  a  handful  of annoying  compatibility  issues  that,  while  not  show&#8208;stoppers, can make life more difficult than it needs to be.  

---

### Post by Hakunka-Matata on 2010-10-11
AMD64 Processors

I have an AMD64 processor, should I install the i386 ISO or the amd64 one? What are the drawbacks of having an amd64 install?

AMD64 is an officially supported architecture with its respective ISO for Ubuntu and all major Ubuntu derivatives. By installing the amd64 ISO, rather than the i386 (32-bit) ISO, there will be some enhancement in performance.

The drawbacks are that Ubuntu, with APT (the package manager for Ubuntu), currently does not support BiArch, which means you likely won't be able to install and run 32bit packages automatically with programs like apt-get, aptitude, and Synaptic on your AMD64 install. This is a problem for users who wish to use some application that is only available for 32-bit. These are rare but do exist. There are possible methods of getting it running, but they involve either copying in the files manually or creating a chroot (see DebootstrapChroot), for example. 


[https://help.ubuntu.com/community/CommonQuestions]("https://help.ubuntu.com/community/CommonQuestions")

Good short read - from above link

---

### Post by Ranger_Joe on 2010-10-11
Ok, gotcha. Makes sense. Glad I have the 32 installed.

---

