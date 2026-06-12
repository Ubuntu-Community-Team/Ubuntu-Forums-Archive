---
title: "Kernel Update went south"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Saint_ on 2009-05-26
Ok so I've been booting/running Kubuntu 8.10 just fine, been getting excellent system performance (kernel: Ubuntu 8.10, kernel 2.6.27-11-generic) But quite recently there was an update to Ubuntu 8.10, kernel 2.6.27-14-generic, so I downloaded and let it install. After restarting and trying to boot with the new kernel I found that it didn't work, don't know if it was a graphics driver problem or what, but the splash screen was basically non-existent. All that showed up was a bar of pixels at the top of my screen. After control+alt+backspacing i figured out that it had infact booted to the login screen, but still nothing was visible (save for that bar of pixels at the top). I also ran this version in recovery mode and everything checked out. So I went back to booting to the previous kernel, thinking no harm done. But ever since that update my CPU's have been idyling literally 50% higher, as if it were running both kernels or something. So now my proformance has slowed by about half, which is bothersome to say the least. I'm thinking about formatting and reinstalling to see if that solves the problem, but if anyone has any advice or knows how to remedy this, it would be greatly appreciated. Thanks in advance.

---

### Post by b@sh_n3rd on 2009-05-26
All you did was update the kernel right?...well even though it does seem like a video problem, there doesn't seem to be a reason for it to go wonky for a new kernel...and even if it DID go wonky just for the *new* kernel, it *should* work on the old...After trying the older one, can you get to the login screen? It's abit vague right there...

If you were upgrading your version of ubuntu, we could say directly that it's video...but here it's puzzling...I've tried more than 3 kernels uptil now and even though I've noted a few different bugs on each when run on my pc, all of these bugs vanish with the default kernel...and no other change like your performance regression...I'm using Jaunty though...

---

### Post by Saint_ on 2009-05-26
Ah yeah it's crazy **** man lol. Yeah I'm currently running the older kernel (8.10) and I mean i can log in and work, etc everything runs, it's just my CPUs idle WAY too high and even little things like deleting files will nearly max them out. But yes, I can login via the older kernel.

Also, I'm using a custom distro my friend hooked me up with, which is actually running a Gentoo kernel. So that might be why the newer one doesn't work. Thanks for the reply man

---

### Post by b@sh_n3rd on 2009-05-26
> **Saint_ said:**
> Ah yeah it's crazy **** man lol. Yeah I'm currently running the older kernel (8.10) and I mean i can log in and work, etc everything runs, it's just my CPUs idle WAY too high and even little things like deleting files will nearly max them out. But yes, I can login via the older kernel.

Also, I'm using a custom distro my friend hooked me up with, which is actually running a Gentoo kernel. So that might be why the newer one doesn't work. Thanks for the reply man

Gentoo kernel? how on earth did you get that to work with Ubuntu in the first place?? :D...hmm...I suppose that just makes things complicated, nevertheless, it's probable the update failed coz of an alien kernel...I think you'd better wait around for some one else's reply...

---

### Post by Saint_ on 2009-05-26
You know I honestly can't tell you, my friend rigged it up lol. But thanks for your help man, if all else fails i'll spend my day tomorrow reinstalling and tuning everything up not like i got **** else to do.

---

### Post by b@sh_n3rd on 2009-05-26
*if* you are reinstalling...don't you like to take the step to Jaunty? ok, it may have some bugs in it but only for Intel I suppose...oh yeah and ext4 is ok, but supposed to have it's up's and down's too, but i'm set for xfs (it's as fast as ext4 and disk throughput is better than any other fs). I've got an Intel card anyways :D....it's working quite perfectly after a small fix...overall, Jaunty's good...very fast too (especially with ext4 or xfs, haven't tried ext3 on it)...after using it...I can't dream of using Intrepid (any older ubuntu release) if ever I have to :D

---

### Post by Saint_ on 2009-05-26
I did think about upgrading to Jaunty, but after looking over the forums I saw a ton of posts claiming errors when it came to AMD cards. Also, since I'm running a Gentoo kernel wouldn't Jaunty flip **** on me?

---

### Post by b@sh_n3rd on 2009-05-26
> **Saint_ said:**
> I did think about upgrading to Jaunty, but after looking over the forums I saw a ton of posts claiming errors when it came to AMD cards. Also, since I'm running a Gentoo kernel wouldn't Jaunty flip **** on me?

Jaunty uses the 2.6.28-11-generic kernel by default...It shouldn't flip on you if you try a clean install...(formatting /boot at least). I'm currently running the 2.6.30-rc7 kernel to run my Intel card to the max. I've also got the 2.6.29 kernel just in case. The default, 2.6.28, can't be removed but that's good coz my system loads like a dog on adrenaline (quoted from a true incident) with that :D

---

### Post by Saint_ on 2009-05-26
Hm, alright i'll definitely give it a shot then. Hell if it performs better then I'm in lol

---

