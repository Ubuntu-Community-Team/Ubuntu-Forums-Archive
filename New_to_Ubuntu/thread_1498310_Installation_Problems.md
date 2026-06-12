---
title: "Installation Problems"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by spaghead on 2010-05-31
I am installing Ubuntu for the first time and having real problems.

During the installtion the screen blanks and after various amounts of disk activity... nothing. When i get the boot options menu there is no safe graphics mode available, i have also selected various "vga=" options but the same results.

I have looked through the forums and found no exact match and have tried a number of variations to fix it.

I have a fujitsu siemens Lifebook P7010.

---

### Post by nhasian on 2010-05-31
can you specify which version of ubuntu your using?  10.04?  liveCD? Have you tried the alternate CD instead?

if your CPU supports 64 bit, then please use the 64bit version of ubuntu.

---

### Post by sidzen on 2010-05-31
Please do as the beer milkshake-loving [nhasian]("http://ubuntuforums.org/member.php?u=566669") asks, in the meanwhile . . .

I looked through the following page after googling your system:
[http://wiki.archlinux.org/index.php/Fujitsu_Siemens_Lifebook_P7010#System_Specifications](http://wiki.archlinux.org/index.php/Fujitsu_Siemens_Lifebook_P7010#System_Specifications)
And if Arch recommends the video modifications it does, it is no wonder you are having problems with full-blown ubuntu.

I would suggest either maxing out your RAM capacity and going with either*** lubuntu*** or the netbook remix (**NR**) of any flavor of ubuntu, or . . .  going with another Debian-based distro like ***antiX*** . . . or going with an independent distro like Arch or Igelle.  

I'm playing no favorites here, but this _is_ an ubuntu forum.  Just trying to help and . . .
Best wishes!

---

### Post by nhasian on 2010-06-01
oops, i didn't realize that fujitsu siemens Lifebook P7010 = 6 year old laptop.  yeah if you only have 512M ram then you probably want to go with Lubuntu instead.

---

### Post by Akumuo on 2010-06-22
When you get to the point that you can enter command-line options for the installation just add: xforcevesa
Should work.

---

