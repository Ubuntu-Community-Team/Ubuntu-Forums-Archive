---
title: "More than occasional mouse freeze at start-up"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by al.adab on 2009-08-03
hello,

I'm using Ubuntu 9.04 on a Dell Vostro 1310. Everything works flawlessly. Every now and then, though, the laptop's mouse freezes at start-up. 

When it happens, the cursor just stands still in the middle of the screen and all I can do is to press the power button to re-boot the machine. 

Usually it doesn't happen two times in a row. I noticed it happens regardless of whether or not the power cable is plugged in. 

Any idea? Thanks.

---

### Post by mprince on 2009-08-03
This page may have something you can try:

[http://vanitdiscovery.blogspot.com/2009/05/ubuntu-904-keyboard-and-mouse-problem.html](http://vanitdiscovery.blogspot.com/2009/05/ubuntu-904-keyboard-and-mouse-problem.html)

---

### Post by al.adab on 2009-08-09
Thanks for the tips. Did try but somehow failed to fix it. Migrated to Linux Mint 7 in an impromptu decision. It works flawlessly. Highly recommended :)

---

### Post by al.adab on 2009-08-11
...and come back to Ubuntu (Mint...well...) + given one more try to apply the solution given. So far so good, re-booted a few times and it doesn't seem to freeze any longer.

---

### Post by dansee on 2009-09-08
I played around with adding lines to "menu.lst," and other suggestions.  However, the solution that really worked best was to simply install a new kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

2.6.28 just didn't want to play nice with my Vostro 1310, but it flies w/2.6.30

---

