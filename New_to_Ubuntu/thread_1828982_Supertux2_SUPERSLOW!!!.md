---
title: "Supertux2: SUPERSLOW!!!"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-19
I have a fancy freaking computer, with 4 gigs of ram, an awesome graphics card, and just plain awesomeness, and yet... running supertux2 makes me want to die. Its soooo slow, I have to make the window so itty bitty, like 300x300 just to get it to work... I want it full screen D:!

I ran this in terminal, if it helps. Its the only thing I could find googling and the person who asked had a no on the rendering...
```

alyssa@alyssa-HP-G62-Notebook-PC:~$ glxinfo | grep rendering
direct rendering: Yes
alyssa@alyssa-HP-G62-Notebook-PC:~$ glxgears
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1780 requests (41 known processed) with 0 events remaining.
alyssa@alyssa-HP-G62-Notebook-PC:~$ 

```

Heres my info using sysinfo xD

```

Ubuntu 11.04
Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
1200.000 MHz Frequency
L2 Cache - 1024 KB
Memory total 2955 MiB (Wait, I thought I had 4gigs?!? Did I lose one?)
Swap total: 7628
VGA Compatible Controller: Intel Corporation Mobile 4 series chipset integrated graphics controller 


```


Any helps appreciated. thansk <3

---

### Post by uRock on 2011-08-20
Are you running 32 or 64bit?
> **Lucypie said:**
> 32 bit Ubuntu, 64 bit Windows 7... I hope that I wasn't supposed to get 64B ubuntu cause of windows.. xD
32bit won't see all of the RAM is all. I am not sure of the problem, which is why I didn't create a new post and up the thread's post count.

---

### Post by Lucypie on 2011-08-20
32 bit Ubuntu, 64 bit Windows 7... I hope that I wasn't supposed to get 64B ubuntu cause of windows.. xD

---

### Post by Keith_Beef on 2011-08-20
> **Lucypie said:**
> 32 bit Ubuntu, 64 bit Windows 7... I hope that I wasn't supposed to get 64B ubuntu cause of windows.. xD

It's not that you should get 64-bit Ubuntu because of windows, but that you should get a 64-bit OS because you have a 64-bit T4500 CPU.

But I think that's not the real reason for your rendering problem.

Added:
I just took a look at the Wikipedia page on "[Intel Pentium Dual-Core microprocessors]("http://en.wikipedia.org/wiki/List_of_Intel_Pentium_Dual-Core_microprocessors")". The T4500 CPU looks like it is destined for laptops; you mention that you have a "VGA Compatible Controller: Intel Corporation Mobile 4 series chipset integrated graphics controller"... I think that's where the problem is. Try searching the forum for your particular video controller, and see what you can turn up. Hope that helps you.

---

### Post by Lucypie on 2011-08-20
I don't udnerstand. Search for what? Drivers? Do I have to have a 64bit OS or can I stick with this? I really don't want to mess this up, and besides, dad has a 32 bit and I have to give him everything so he doesn't eat the internet. i would prefer to stick to 32

---

### Post by Keith_Beef on 2011-08-20
> **Lucypie said:**
> I don't udnerstand. Search for what? Drivers? Do I have to have a 64bit OS or can I stick with this? I really don't want to mess this up, and besides, dad has a 32 bit and I have to give him everything so he doesn't eat the internet. i would prefer to stick to 32

You can use 32-bit Ubuntu with a 64-bit processor, but as uRock pointed out, you will not be able to use all your RAM with that. To be able to use all your RAM you would have to go for 64-bit Ubuntu.

If you're just downloading things for your dad, then it probably wouldn't matter if you were on 64-bit, except that if the download pages detected your 64-bit OS you might have to click a couple more times to over-ride that to go to a page to download a 32-bit version for him.

But that's really a question for a new thread: 64-bit or 32-bit... I went through that myself.

For your graphics problem, with supertux2 being too slow, I can't be a great deal of help since I don't know much about your particular card. 
Try searching the forums for "Intel  Mobile 4 series glx fatal IO error 11"

---

