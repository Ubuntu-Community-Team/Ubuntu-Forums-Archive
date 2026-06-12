---
title: "Installing a new kernel"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Giraffemonster on 2011-01-28
Hello, I've got some questions concerning installing a new kernel. My current kernel is 2.6.35, generic(i686). I downloaded the kernel archive from kernel.org, 2.6.37. I'm installing it right now using this guide.
[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)

1. I'm currently using the "sudo make" command, and it's taking an ungodly amount of time. Is this normal? I've read the F.A.Q on the site, and it mentions something about 2GB files, however the archive is only 70MB, which is sort of confusing as it's taking this long to process.

2. After this is done, will I have to install new drivers? If so, then audio, video, or both?

3. Is there anything else I should know that isn't mentioned in the guide?

Thanks for reading.

---

### Post by philinux on 2011-01-28
> **Giraffemonster said:**
> Hello, I've got some questions concerning installing a new kernel. My current kernel is 2.6.35, generic(i686). I downloaded the kernel archive from kernel.org, 2.6.37. I'm installing it right now using this guide.
[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)

1. I'm currently using the "sudo make" command, and it's taking an ungodly amount of time. Is this normal? I've read the F.A.Q on the site, and it mentions something about 2GB files, however the archive is only 70MB, which is sort of confusing as it's taking this long to process.

2. After this is done, will I have to install new drivers? If so, then audio, video, or both?

3. Is there anything else I should know that isn't mentioned in the guide?

Thanks for reading.

The question to ask is why are you doing this? What are you trying to achieve?

---

### Post by Giraffemonster on 2011-01-28
Trying to achieve better desktop performance. The hardware I have is pretty outdated, and I don't have the funds to buy anything better. Right now, I'm using a kernel for a generic processor. Apparently, it's faster if the kernel is optimised towards the hardware it is utilising.

---

### Post by TeoBigusGeekus on 2011-01-28
Installing a new kernel could make your whole system hang.
I'm pretty sure you have to recompile your graphics drivers.
Even if all the above succeed, you'll end up with a fragile system, prone to errors and kernel panics.
Instead of taking such radical measures, have you tried Lubuntu?
Or, even, have you tried getting rid of gnome and going with standalone Openbox (to name just one, my favourite, lightweight windows manager)?

---

### Post by Giraffemonster on 2011-01-28
> **TeoBigusGeekus said:**
> Installing a new kernel could make your whole system hang.
I'm pretty sure you have to recompile your graphics drivers.
Even if all the above succeed, you'll end up with a fragile system, prone to errors and kernel panics.
Instead of taking such radical measures, have you tried Lubuntu?
Or, even, have you tried getting rid of gnome and going with standalone Openbox (to name just one, my favourite, lightweight windows manager)?

I didn't know about any negative results from installing a new kernel if done correctly. I also have heard of Lubuntu, but I would prefer to stick with an official distribution of the Ubuntu family. I guess the closest thing would be Xubuntu. I haven't heard of Openbox though.

So I'm guessing that I shouldn't be installing a new kernel. Going to close the terminal now. I haven't ran make install yet though, so I believe no damage has been done. Thanks for helping me avoid that mistake.

---

### Post by TeoBigusGeekus on 2011-01-28
Not a mistake actually... more like asking for it; or, as the greek saying goes, walking without pants among the cucumbers :lolflag:

---

### Post by Paqman on 2011-01-28
> **Giraffemonster said:**
> I didn't know about any negative results from installing a new kernel if done correctly.

I do. The kernel is a crucial part of your system's security. By stepping outside the package manager and manually installing kernels you'll no longer receive important security updates.

That's fine if you want to also subscribe to all the right mailing lists, keep abreast of the security issues, and take responsibility for installing the required updates in a timely manner, but if you ask me that sounds like a lot of hard work for little or no benefit.

If you're looking for a software option to improve performance, i'd suggest looking at switching to lighter apps, or doing a minimal install.

---

### Post by PrivateSNAFU on 2011-01-28
I personally do like building my own kernals and because you can choose which kernel you boot up with in grub its just a question of rebooting the computer to go back to your normal system. But I would recommend another distort, ubuntus updates would break  your custom kernel.  I would personally install slackware on and old computer and experiment, you can get very good performance from it on older machines.  

be prepared to wait a while for a kernel to compile.

good luck and have fun ;)

---

### Post by Giraffemonster on 2011-01-28
Thanks for the additional advice guys, I'll be sure to take it into consideration. Also, I would prefer to have Ubuntu's updates do the mentioned work for me, so no new kernel for me.

I'll take a look at Slackware though, I've heard about it.

---

### Post by cariboo on 2011-01-28
I haven't built a custom kernel in quite a while, but back in the day when I was running a dual cpu pII system, it used to take about 2 hours to compile a kernel. The only reason I built a custom kernel is the default at the time didn't support smp.

---

### Post by hansolo4949 on 2011-01-28
I wouldn't take that step at all, unless you are expecting some big advantages from it. As other people have said, you would pretty much have to hold the entire system together yourself, or else you WILL have some big problems. I would just go to Xubuntu, if you want more speed, or just stay with the latest kernel updates.

Anyway, I hope you have your stuff backed up if you decide to do this!

---

