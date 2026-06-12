---
title: "Hibernate has problems"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by oingk on 2010-03-20
Hi,

Using Ubuntu and the Hibernate functionality doesn't seem to be doing well. When I want to come back from Hibernate it usually takes a really long time to come back, and today it was taking eternally so I had to shut off from the computer's button.

The other thing is that when it comes back from hibernate, before it returns to previous session, when the ubuntu logo is shown, the screen is all scrumbled reminding me of a Windows-on-virus computer.

Can anyone guess what the problem might be?

---

### Post by 1915flyer on 2010-03-20
I can't help with your specific problem, but the first thing you need to do is post some information about your system - brand and model, processor, memory, video card. It may be a known problem with your model computer.

---

### Post by Helkaluin on 2010-03-20
Several ideas for your problems:

1. First we should establish that hibernate is possible. Seeing that you mentioned resuming being too long, I'd assume it is possible. Nonetheless it doesn't hurt to confirm that your swap partition is at least bigger than your RAM size. It is always better to have a swap just a little bigger just in case the system doesn't have to flush data already in swap in order to contain the hibernation data from RAM.

2.a The speed issue: The built-in hibernation implementation in Unbuntu (at least as of 9.10) is swsusp <http://en.wikipedia.org/wiki/Swsusp>, which unfortunately doesn't support compression of the hibernation data. When you hibernate, therefore, the system carry out a very basic implementation of hibernation - the data in RAM is copied to the swap as is. Using compression in the hibernation process can very probably speed up the process due to modern system's CPU speed much faster than hard disk read-write speeds. To implement this you could try out uswsusp <http://en.wikipedia.org/wiki/Uswsusp> <http://suspend.sourceforge.net/> which supports compression. To set it up is very easy - the package in even in the Karmic repositories, just install it via Synaptic.

2.b More on speed: If you're adventurous, you might want to try out TuxonIce, which could be even faster than using uswsusp and provides extra stuff as progress of resuming and what-not. You'll need to install patched versions of the kernal, though. But it's all in the TuxonIce repository so it won't be really that problematic. Simply add that extra repository, install the kernal in Synaptic, and run the hibernation installation script you can find on the website. <http://en.wikipedia.org/wiki/TuxOnIce> <http://www.tuxonice.net/>

3. The scrambled ubuntu logo: If I'm assuming correctly, I think you mean the white logo turning into something that has weird colours around it, right? In that case, use StartUp-Manager (find it in the official repositories) and change your splash screen (usplash, to be specific) to fit your desktop resolution and colour depth.

---

### Post by oingk on 2010-03-25
Sorry for taking so long to reply, I still hve the problem but I was too busy to deal with it.
> 
 I can't help with your specific problem, but the first thing you need to do is post some information about your system - brand and model, processor, memory, video card. It may be a known problem with your model computer.

It's a Lenovo ThinkPad SL500, has a Intel Core Duo processor (2.2GHz), and 2GB RAM. I have only Ubuntu 9.10 installed on it.
> 
1. First we should establish that hibernate is possible. 

I guess it does hibernate when I make it to hibernate, and it only has a problem waking up.> 

Nonetheless it doesn't hurt to confirm that your swap partition is at least bigger than your RAM size. It is always better to have a swap just a little bigger just in case the system doesn't have to flush data already in swap in order to contain the hibernation data from RAM.

What's a swap partition?

Regarding the other things you said, I'm still processing them in my mind. I will hibernate my computer right now so that I'll come back here and tell you details of what happens.

---

### Post by oingk on 2010-03-25
OK so when I clicked on hibernate the screen went blank and the laptop made some growling noise and seemed unresponsive. 

Then I pressed a key and it showed as if coming back to life but after 2 seconds it shut down completely. 

I pressed the power putton and as it was going on it gave a scrambled screen. This was apparently not a scrambled logo, but something random and indistinguishable. Say for example something like the picture here: [http://www.arcaderestoration.com/graphics/repair/williamscpupcb1big.jpg](http://www.arcaderestoration.com/graphics/repair/williamscpupcb1big.jpg)

Then it woke up normally and wasn't so slow in doing so this time.

---

