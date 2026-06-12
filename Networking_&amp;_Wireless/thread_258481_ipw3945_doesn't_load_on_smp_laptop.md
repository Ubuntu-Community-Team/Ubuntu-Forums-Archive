---
title: "ipw3945 doesn't load on smp laptop"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Komissar on 2006-09-16
Well I'm stumped, and I need some assistance. Has anyone run into this problem. I've got an ipw3945 card builtin with my Dell XPS-M1710, running the intel core duo at 2.16Ghz. So I install from the ubuntu live cd and I have a working network card. Now I decide it would be great to use the cpu as it was meant to, run as an SMP. So I download the latest kernel through synaptic. I went from 2.6.15-23-386 kernel to 2.6.15-26-686. Now the card isn't even recognised. I've been pouring over the various threads, and tried a few, but no joy. Has someone over come this somehow? I would appreciate any help to solve this without reinstalling. Thanks..

---

### Post by intermilo on 2006-09-16
have the same card on my gateway laptop, upgraded to 686 also from 386 and my card also vanished, been looking for solution, but no success, i would also appreciate any help

---

### Post by ltmon on 2006-09-17
Hi All,

It's most probably due to missing the linux-restricted-modules package for your kernel version.  The ipw3945 card needs a non-free daemon that's in this package.

Have a look at my post in this thread to get it working: [http://ubuntuforums.org/showthread.php?t=244814](http://ubuntuforums.org/showthread.php?t=244814)

---

### Post by Komissar on 2006-09-17
Ok! Wow, THANKS Itmon, I thought I had tried it all, but that tip really helped. Here's all I did to finally get my wifi working:

1. I booted up in 386, so the ipw3945 would be useable.
2. I opened synaptic and went to the Section, Base System and selected
    linux-image-2.6.15-26-686.47
3. I then went to Base System (restricted) and selected
    linux-686-smp
4. Then a reboot using 2.6.15-26-686 and to my surprise a little green wifi light went on indicating a perfectly working ipw3945. Thanks again for pointing me in the right direction. :D

Now I can feel the speed again and not have to dual boot linux, which I felt was a little too weird.

---

### Post by intermilo on 2006-09-17
worked perfectly for me, too. thanks a lot

---

### Post by ntg on 2006-11-02
Thanx guys! Nice tip! A point though: I think the best to do is install the 
package: linux-restricted-modules-686 
so as to get security updates etc...
My wifi and smp work at the same time by just installing a package:) Wow!

---

