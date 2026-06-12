---
title: "Ubuntu Sucking (Slow boot times, Graphics Problems, and Mouse/Keyboard Problems)"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by 2soos2 on 2011-06-27
NOTE:  I've installed all updates, so that shouldn't be the reason.
This is probably my fifth day with Linux (Ubuntu 11.04), and although I was impressed the first day, I'm thinking of permanently reverting back to Windows.
Here are some reasons:  
I was told that Linux had very quick boot times, but this is not the case. I timed how long it takes from turning on the computer to logging in to the desktop.
For Ubuntu 11.04 it takes me around 40-45 seconds or so to turn on the computer and log in.
For Windows 7, this takes me around 25-30 seconds.
Besides the slow boot times, some applications are running sluggishly slow.
I tried installing Docky, and it lags horribly.
Moreover, I installed Super Tux Kart, and although it runs nearly perfectly, it seems to be using too much CPU. I think it gets to the point where the computer heats up too much and Linux automatically shuts down the computer. So it seems applications aren't being run efficiently.
My hardware isn't too shabby considering what some other Linux users have.
My processor is a Core 2 Duo 2.0 Ghz and I have 4 Gigs of DDR2 RAM, along with a 512 MB dedicated nVidia GPU.

I'm encountering many Graphics problems when I lock my screen, suspend/hibernate, switch user, or even when trying to shut down the computer:  
Check the attached picture.

Finally, I'm encountering a really irritating problem concerning my mouse and keyboard. They simply freeze sometimes and stop working and the only way to solve this is either to reboot which takes a while or to suspend which runs me into the graphics problem.
Please see this thread:  [http://ubuntuforums.org/showthread.php?t=1788822](http://ubuntuforums.org/showthread.php?t=1788822)

In summary, I'm not at all impressed with Linux, and I'm not even able to see why there's such a huge community for it if it's this bad for everyone. If it's not this bad, then could someone please help me solve my issues?
Thank you.

---

### Post by b@sh_n3rd on 2011-06-27
Hi, my apologies for the problems you're encountering. As far as I can  see, your problems might be attached to a buggy video driver. Are you  using proprietary video drivers or vesa drivers? Since you've got an  nvidia card, you've got the upper hand. Vesa, sometimes, sparks. Even  the keyboard and mouse thing. I suggest we get first things first. That's, video. If video's down, lot's of things get haywire. Even on windows.

Slow boot times is rather strange coz Ubuntu is even faster than my own custom build of linux. And speaking of which, the community exists because some of us just like to maintain our own systems and create our own fixes, like myself. I'd suggest you watch what you say because, people are less likely to help you if you think insisting on dropping Ubuntu is going to do anything. It's not a religion man so it's not gonna hurt anyone. It's just a matter of choice.

Anyway, I'm not one to debate. Vesa or Proprietary Drivers?

---

### Post by el_koraco on 2011-06-27
Ubuntu 11.04 has much longer boot times than the predecessors. Your problems seem to be realted with the GPU. Can you open the Dash (Super key, or the upper left button), enter "Additional drivers", open the program and see what it says? There should be an option to install Nvidia's drivers?

---

### Post by amjjawad on 2011-06-28
> **2soos2 said:**
> In summary, I'm not at all impressed with Linux, and I'm not even able to see why there's such a huge community for it **if it's this bad for everyone**. If it's not this bad, then could someone please help me solve my issues?
Thank you.

It's perhaps bad for **you** not for **everyone** ;)

If I were you, I would spend more time on google search better than keep complaining.

I see your frustration but that will take you to no where. Take it easy and if "you" think that you did your fair share of searching and learning a totally new world ([Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")), then there must be something wrong somewhere. For me, I don't mind to learn Linux for 10 years than waste one hour with Windows but that's only me :)

NO OS IS PERFECT, PERIOD. << That is rule no.1 that "everyone" must be aware of :)

Good luck!

---

### Post by beew on 2011-06-28
Actually even without installing the Nvidia driver Ubuntu 11.04 is pretty fast and smooth (I have one Natty install that uses only nouveau 3d and another with the proprietary driver). It takes longer to boot than 10.10 (to load Unity)  but still a lot faster than Vista (10.10 is faster than WIn7).

So it seems like the problem is with the hardware. Is it a laptop or a desktop? If it is a laptop does it have Optimus enabled?

---

### Post by alphacrucis2 on 2011-06-28
At least when you login to ubuntu it is immediately usable. After logging in to Windows 7, I go and make myself a cup of tea. With luck it will be usable by the time I am done.

---

### Post by Mark Phelps on 2011-06-29
Sorry, don't have a solution for your long boot times -- but I share your concern.  Ubuntu 10.10 took a longer thatn 10.04, and failed to boot so often, that I came to interpret long times as boot failures.

After I installed 11.04, it took even LONGER to boot -- so I made the mistake of make the same interpretation.  But the, I let it go once and it DID boot -- eventually.

And NO, before anyone implies it, I do NOT have a slow machine.  This is a six-core AMD 1090T with DDR3 1600 memory -- and it boots into Win7 (and gets me a working desktop) in a fraction of the time that it takes to boot into Ubuntu 11.04.

---

