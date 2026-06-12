---
title: "Should I recompile the kernel for my specific processor?"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by jcjveraa on 2011-05-30
I've just finished up installing Lucid on my HP thin client, using the netinstall of the i386 version. My device has a pretty obscure 800MHz Transmeta Crusoe processor on board. I've read on the web that it is possible to recompile the linux kernel and setting the processor type to Crusoe. I've also found guides [such as this one ]("http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html")which help you through the recompilation process allowing you to just change one thing about the kernel by compying the current settings (for safety).

My question: will recompiling the kernel for my specific processor improve the general or CPU performance of my system? This would seem to me to be true, why else is the option there, but I'm not sure and I can't find much about this subject (i.e. I must be looking in the wrong places :)

Thanks!

---

### Post by dFlyer on 2011-05-30
With linux you can do almost anything you want. I believe if it ain't broken, why fix it. But than again I learned a lot about linux by braking things and having to fix it. The choice is your.

---

### Post by lisati on 2011-05-30
Although I haven't tried compiling a kernel, I suspect that it would be a good way to learn.

Other than the opportunities to learn something, one potential advantage I see would be to help the performance of the OS.

---

### Post by jcjveraa on 2011-05-30
Thanks, I'll just give it a go then :)

---

### Post by wildmanne39 on 2011-05-30
> **jcjveraa said:**
> Thanks, I'll just give it a go then :)
Hi, I did compile one in gentoo and it was a task but a good learning experience.

---

### Post by tgalati4 on 2011-05-30
I recompiled my Jaunty kernel to activate undervolting on my Pentium-M.  It took about 2 hours the first time and 1.25 hrs the second time.  I cut out a bunch of crap that I wasn't using and it shrunk the kernel and it seems slightly faster.  I've read that you can get a 2% performance improvement, but it depends on your workload and how you use the machine.  I set the tick to 100 Hz to allow the CPU to sleep more.  You can set it to 1000 Hz to get a more responsive mouse/keyboard feel.

You will have to run your own benchmarks to determine if there are speed improvements.

And if you break it, you get to keep both pieces.  (Or boot into a previous kernel.)

---

### Post by jcjveraa on 2011-05-31
We'll I just started to give it a shot a couple of hours back. It's steadily doing stuff since I gave the make command. There are some warnings* every now and then, but no errors yet (at least none that make it stop compiling ;)).

Since I'll have both kernels available, I'll run some tests afterwards to check for any perfomance differences.


* Example of warning:
```
include/linux/async.h:20: note: expected âvoid (*)(void *, async_cookie_t)â but argument is of type âvoid (*)(struct acpi_device *, async_cookie_t)â

```

---

### Post by Paqman on 2011-05-31
> **jcjveraa said:**
> 
My question: will recompiling the kernel for my specific processor improve the general or CPU performance of my system?

It's far from guaranteed. When you compile a kernel from scratch, there are a *lot* of options you can choose. Unless you know exactly what they all are it's very easy to end up with a kernel that's sub-optimal.

Have a go by all means, but don't expect to get miraculous results first go. You're probably going to need to have several attempts at what is quite a slow process, and you'll probably need quite a bit of input from people who know a lot about kernels.

---

### Post by jcjveraa on 2011-05-31
> **Paqman said:**
> It's far from guaranteed. When you compile a kernel from scratch, there are a *lot* of options you can choose. Unless you know exactly what they all are it's very easy to end up with a kernel that's sub-optimal.

Have a go by all means, but don't expect to get miraculous results first go. You're probably going to need to have several attempts at what is quite a slow process, and you'll probably need quite a bit of input from people who know a lot about kernels.
Thanks for the reply. If I understood the tutorial I followed correctly, I should be compiling the kernel mostly as it is right now and not really 'from scratch', by copying the current kernel's config file.

In mkconfig I loaded the copied file, and only changed the 'processor family' option from the current one (iirc 586/K5/5x86/6x86/6x86MX) to 'Crusoe' (like in the list [over here]("http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch09s03.html")). Any thoughts on that?

---

