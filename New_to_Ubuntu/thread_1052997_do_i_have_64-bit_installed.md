---
title: "do i have 64-bit installed?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by unitedwefall on 2009-01-28
Hi

OK so i just got a dell xps m1730 and it has 4Gb of ram; i wanted to make the most of the system on linux but i had got a lone of the ubunti 8.10 live cd from a friend. He was saying that when you install it it will install the right build for your system. However when i go to system moniter it says i ont have 3gb of ram. Is that because the 32-bit build has installed? can i change it? haha sorry if i sound an idiot, even in the absolute beginers forum this seems a silly question.

Thanks xx

---

### Post by binbash on 2009-01-28
yes you have 32 bit installed.you can see the kernel with uname -a .64 bit and 32 bit versions are different isos.you can download and install 64 bit one.(you have to delete current install if you want to install 64 bit.However you can fix that ram problem - check tutorial forum for that- and keep the 32 bit install since 32 bit is more stable at my system)

---

### Post by ptn107 on 2009-01-28
I have been using Ubuntu 64-bit since 7.04 without any problems.  It's stable.  Flash has sometimes been a problem for 64-bit pre Ubuntu 8.04 but those issues have been solved since.

[_Ubuntu 8.10 64-bit_]("http://releases.ubuntu.com/intrepid/ubuntu-8.10-desktop-amd64.iso")
[URL="http://releases.ubuntu.com/hardy/ubuntu-8.04.2-desktop-amd64.iso"][U]
Ubuntu 8.04.2 LTS 64-bit[/U][/URL]

---

### Post by bongey on 2009-02-22
Anyone who has a dell m1730 with dual 8700M gt cards running ubuntu ibex, can you post the out put of lspci |grep VGA .  (my kernel is    2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 . from uname -a ) 

I think one of may cards has gone to video card heaven. Can't enable sli in ubuntu, I even booted an old windows image that haven't touch in a year , and it couldn't detect the second card either.

---

