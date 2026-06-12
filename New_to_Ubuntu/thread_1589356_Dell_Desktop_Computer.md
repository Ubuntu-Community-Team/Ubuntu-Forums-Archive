---
title: "Dell Desktop Computer"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by cool_penguin on 2010-10-06
Hi everybody,

I have been using Ubuntu for the past four years and this is the first time, I am really running into trouble. I recently got myself a Dell XPS Studio 7100 desktop computer at work. As usual it came with Windows 7, which I wiped clean and installed 64 bit Ubuntu 10.04. This system has an AMD Athlon II Quad core processor, ATI Graphics, 6 GB RAM and a 500 GB HDD (7200 rpm). These specs are very good and should run Ubuntu very well. While it does work well most times, I often find my computer freezing randomly. Sometimes, it freezes and I am unable to move the mouse or do anything on the keyboard and sometimes it freezes suddenly with a dark black screen. The only option I am left with is to hard boot the system using the power button. Every time I do that I hear the hard drive make a click sound and I am really worried that I am damaging the hard drive. Any help from you guys will be greatly appreciated.

Thanks very much for reading my post.

I am looking forward to hearing from you.

Have a nice day.

Cheers,
Harry

---

### Post by cascade9 on 2010-10-06
I've had computers with undersized power supplies do that. It could also be your video drviers.

---

### Post by amauk on 2010-10-06
sounds like either a power supply or a heat issue

---

### Post by cool_penguin on 2010-10-06
Thanks guys for your prompt response. I am using the default video driver that comes with Ubuntu 10.04 (not the restricted driver). I just opened the CPU cabinet and the fan seems to be spinning just fine. Although as compared to Intel systems, the fan seems slightly slow. When I touched the heat sink, it did not feel warm and so i am assuming that the fan is doing its job. 

Any other ideas/suggestions?

---

### Post by cascade9 on 2010-10-06
I'd give the ATI drivers a go..cant make things worse. (well, possibly it could, but then you can just remove the drivers). 

I dont think it would be heat, but a neat, 'dirty' tirck for that is to remove the side from the case, point a desktop into the case, turn it on at full blast blowing into the case. 

Its not 100% accurate though.

---

### Post by cool_penguin on 2010-10-06
Thank you for your suggestion. I will give the ATI driver and go and see if there is any improvement. I will report back. 

Now I wish I had chosen a NVIDIA graphics card or even an Intel graphics for that matter. 

Cheers,
Harry

---

### Post by cascade9 on 2010-10-06
> **cool_penguin said:**
> Now I wish I had chosen a NVIDIA graphics card or even an Intel graphics for that matter. 

Cheers,
Harry

Dont say that till you know its the drivers causing the problem. ;) 

Also, Intel graphics with AMD? apart from fairly rare, very old and just plain horrid intel i740 video cards, not possible.

---

### Post by bprins on 2010-10-06
Hi Harry,

Not an expert on this but got some ideas as well.

First, I wouldn't worry too much about the HDD. They can handle power offs pretty well these days :-).

Second, I had a laptop that froze up or rebooted at random (was a heating problem). What I learned from that, is:
a) removing dust from your PC is better in general :-)
b) BIOS updates are released with a purpose (thus, check if you can update your BIOS)
c) linux pawns with Log-files. All the problems that occurred just before the hangups / reboots were written down in messages / kern.log etc. So keep track of the times that you run into issues and dive in your log files. When you find stuff, google is your best friend.

Hope it helps. 

Oh, and just before you make the same mistake, be careful with updating your BIOS, during the update process my laptop became overheated again, rebooted, and bye bye laptop :=). A very good excuse to buy a new one of course :P.

Cheers,.

Bas

---

### Post by Mark Phelps on 2010-10-06
According to Google, that machine comes with an AMD HD5870 card, which would be good news, but the newer HD58xx cards are having problems with the ATI drivers.

You should do a search in the Video forum on 5870 and see what you find regarding problem corrections.  I think some folks have been able to fix the problems using a driver ppa.

---

