---
title: "Quick kernal patch question (READ THIS ONE guys!)"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-01-18
Sorry about the multiple postings, I don't know if it is my browser or the ubuntu forum itself, but when I was trying to post this question it was spazzing out.

Does anyone know when Ubuntu will get the  four-line kernel scheduler patch that showed up last November. I've been playing around with Linux Mint Debian and it is very, very, very fast. I can't wait for my favorite Linux distro (being Ubuntu) to get it!

---

### Post by ridetheteapot on 2011-01-18
I don't know which patch is this one?
There is that 120 line kernel patch, and bf-scheduler, and the 4 line alternative to that 120 line kernel patch.
that alternative method isn't a patch and you could apply it really easy right now if you wanted - thats not what you mean is it?

---

### Post by sandyd on 2011-01-18
> **skyzthelimit230 said:**
> Sorry about the multiple postings, I don't know if it is my browser or the ubuntu forum itself, but when I was trying to post this question it was spazzing out.

Does anyone know when Ubuntu will get the  four-line kernel scheduler patch that showed up last November. I've been playing around with Linux Mint Debian and it is very, very, very fast. I can't wait for my favorite Linux distro (being Ubuntu) to get it!
you can get it right now.
its in mainline.

---

### Post by skyzthelimit230 on 2011-01-18
This is the one I am thinking about: 

[http://blogs.computerworld.com/17371/the_linux_desktop_may_soon_be_a_lot_faster](http://blogs.computerworld.com/17371/the_linux_desktop_may_soon_be_a_lot_faster)

:D

---

### Post by skyzthelimit230 on 2011-01-18
> **sandyd said:**
> you can get it right now.
its in mainline.

Can you elaborate? I'm a newbie to Linux(only been using it for about 6 months). What is Mainline?

---

### Post by sandyd on 2011-01-18
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)
download correct architecture, install, and enjoy.

You might wanna get 2.6.37 if your using the OSS drivers, there were some major improvements to (I think it was, im going to have to clarify with handy) to dri performance.

---

### Post by ridetheteapot on 2011-01-18
pulseaudio guy's solution is simpler and easier to implement ---- check out [http://blog.christophersmart.com/2010/11/19/miracle-patch-out-performed-by-four-lines-of-bash/](http://blog.christophersmart.com/2010/11/19/miracle-patch-out-performed-by-four-lines-of-bash/)

---

### Post by tobier on 2011-01-18
> **skyzthelimit230 said:**
> Sorry about the multiple postings, I don't know if it is my browser or the ubuntu forum itself, but when I was trying to post this question it was spazzing out.

Does anyone know when Ubuntu will get the  four-line kernel scheduler patch that showed up last November. I've been playing around with Linux Mint Debian and it is very, very, very fast. I can't wait for my favorite Linux distro (being Ubuntu) to get it!

You can always build the kernel yourself, instead of waiting for the Ubuntu team to build it for you. It's not that hard at all.

---

