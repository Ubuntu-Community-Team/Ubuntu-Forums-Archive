---
title: "graphics card problems in 11.04.....and now in 11.10"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by Smithie on 2011-06-03
So, my upgrade from 10.10 to 11.04 went poorly, and my dual screen PC set-up became a complete mess of frozen images and non-working icons.  I believe this was largely due to issues with my ATI graphics card (model RV370 5b60, Radeon X300), and compatibility with....something in the Natty package that I don't completely understand.  I was able to getting the system working in ubuntu classic, but, instead of leaving well enough alone, I attempted to solve this problem myself.

I read something that claimed the kernel in the 11.10 package was better with some of the graphics card issues which sounded like mine, so I went for it.  But, no luck.  I'm having the same problems, and in fact, the graphics issues are even worse.

Now I am using Gnome classic in ubuntu 11.10 alpha and am seeking help with how to get out of this...

So, is there a simple way to downgrade to 11.04 from 11.10 so I can at least use ubuntu classic?

Or, even better, is there a fix for my graphics compatibility problem which will  solve issues with either package in the 11.-- series, so the Ocelot package will work for me?

I'd rather not do a fresh install so I can keep my settings, etc., but I am willing to as a last resort.

---

### Post by wolfen69 on 2011-06-03
> **Smithie said:**
> 

I'd rather not do a fresh install so I can keep my settings, etc., but I am willing to as a last resort.

You can always backup your most used config files from home, such as .mozilla/.thunderbird/ etc..... shouldn't be that big of a deal.

---

### Post by Rex Bouwense on 2011-06-03
My man, unfortunately there is no way to downgrade from one version to the previous.  You must reinstall.  You do know that 11.10 is for testing purposes only and if you are not willing to put up with the daily updates and changes, you shouldn't be using it.

---

### Post by el_koraco on 2011-06-03
Which graphics card driver are we talking about? If you use the proprietary one, you should reinstall 10.10 or 10.04, because when the new xserver comes into the Oneiric repos, you'll have a tough time booting if you use the proprietary driver. 

If things aren't working for your card with 11.04, and you think the new kernel is gonna help, just install the new kernel in 11.04, or simply go back to 10.10. 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

---

### Post by Smithie on 2011-06-03
I checked on the graphics driver and I got "driver=radeon latency=0", a separate check gave me "Radeon X300 PCIE".  Kernel driver was also identified as Radeon.

I am willing to deal with daily updates on 11.10, now that I've already got that package, I don't mind.  My issue is that I can't get out of Gnome "classic" mode without the screens going absolutely haywire, everything from completely blank through to frozen windows which open without being able to close them, and are followed by trails of their own image.  This was the same problem I was having in 11.04 anyway.

I'd frankly rather resolve the graphics issue than go back to 10.10 with a fresh install, it took a long time for this noobie to get a variety of software and hardware things working right in linux, and I'd like to avoid repeating the process/scavenger hunt if at all possible.  In fact, I'd rather replace the graphics card altogether to avoid it if I knew what I needed to get to resolve the problem.

---

### Post by wolfen69 on 2011-06-03
> **Smithie said:**
> In fact, I'd rather replace the graphics card altogether to avoid it if I knew what I needed to get to resolve the problem.

In that case, put an nvidia card in. Nvidia has never let me down as long as you stick to the mainstream cards.

---

### Post by beew on 2011-06-03
Why would 11.10 be even available for "upgrade"?? it is not even alpha and 11.04 still looks like a beta.

And why should anyone be surprised that things don't work???

---

### Post by Bucky Ball on 2011-06-03
As a noob you are likely to have some tough times with 11.10 (not due for official release until October). Make sure you keep a bug-catcher handy! ;)

10.04 LTS or 10.10 preferable, but all depends how steep you want the learning curve. As mentioned, 11.10 is strictly testing at the mo so if you are looking to test and learn and report bugs and problems on Launchpad etc ... great!

---

### Post by wildmanne39 on 2011-06-03
> **beew said:**
> Why would 11.10 be even available for "upgrade"?? it is not even alpha and 11.04 still looks like a beta.

And why should anyone be surprised that things don't work???
Hi, 11.10 became alpha yesterday, I installed it.

---

### Post by Smithie on 2011-06-04
Okay, so, if a new graphics card is my solution, is there any particular low-end dual input (VGA/DVI) nVidia card I should be on the look out for?  Is there a proven model with the 11.-- ubuntu series?

---

### Post by VanR on 2011-06-04
> **Smithie said:**
> Okay, so, if a new graphics card is my solution, is there any particular low-end dual input (VGA/DVI) nVidia card I should be on the look out for?  Is there a proven model with the 11.-- ubuntu series?

Well my $29 Sparkle brand  Nvidia 8400GS seems to work fine.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187100](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187100)

---

### Post by Smithie on 2011-06-04
Well, I won't exactly switch this thread to "solved", but I switched in a new Nvidia graphics card (8400GS).  Now, at least, all my display, monitor, and unity problems with the 11.-- releases are the same as everyone else's......:(

Makes me wish I never left Lucid....lesson learned I guess.

---

### Post by wep940 on 2011-06-04
You can always back up your data, settings, etc., and reinstall lucid.

---

### Post by VanR on 2011-06-08
> **wep940 said:**
> You can always back up your data, settings, etc., and reinstall lucid.


I'm thinking of doing just that myself also.

---

