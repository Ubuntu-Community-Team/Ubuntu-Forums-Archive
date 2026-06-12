---
title: "Memtest error: google shows nothing."
date: 2011-01-31
forum: New to Ubuntu
---

### Post by jd2012 on 2011-01-31
Hi ):P

Working with a fresh install of 10.10. Been trying to diagnose some problems with my HDD so 
I decided to run memtest, ...or not. Came back with an error: "too small lower memory"
"Press any key to continue..." Which takes me back to GRUB.

Any suggestions?

Many Thanks.

---

### Post by khelben1979 on 2011-01-31
Sounds like it could be a problem with your computer hardware, and as you have mentioned, you have already decided to check out the hard drive.

Do you have more hard discs installed which you can test? You might consider changing to another hard disc. [SpinRite]("http://en.wikipedia.org/wiki/Spinrite") is the best software I know of if you want to test the hard disc and also if you were to decide to hide bad blocks from it to prevent them from being used.

---

### Post by ronnielsen1 on 2011-01-31
>                  I couldn't boot into memtest from my lucid install.  I then tried lucid and hardy CDs, but neither worked.
 I then downloaded a memtest iso[1] from memtest.org, and that worked.
 [1] [http://www.memtest.org/download/4.10/memtest86+-4.10.bin.gz](http://www.memtest.org/download/4.10/memtest86+-4.10.bin.gz)

        

[https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429)

Seems to be a bug. You do realize this tests your memory and not any hard drive problems right?

>  Been trying to diagnose some problems with my HDD so 
I decided to run memtest,

---

### Post by jd2012 on 2011-01-31
> **ronnielsen1 said:**
>  You do realize this tests your memory and not any hard drive problems right?


Hi, 

Yea I realize that, apologies, I shouldve been clearer, im also trying to test my RAM, I suspect hardware failure. Upon opening my box i realized that I only have 1 stick of RAM, 1gb, so that means I have 2gb integrated into the mobo. Hopefully thats not going bad :mad:

But thanx for the reply ;)

---

