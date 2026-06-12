---
title: "GPU Overheating Rapidly?"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by K25125 on 2010-11-03
For quite a while (at least since last December), my GPU has had insane overheating issues (as in, 110*C overheating). I suppose I should explain:

Last year (when I still used Windows), I picked up a copy of GTA IV, a graphically-intense PC game. While playing, I used a program to monitor my fan speed; the system would quickly hit 110*C, followed by a huge drop in performance to cool down to 100*C, then increase again. It didn't really bother me for a while, so I dealt with it.

By March, I had been playing a less graphically-intense game with the same issues. I then decided to get it serviced. To my surprise, I was still under warranty. So, I brought my computer to GeekSquad and decided to demo the issue to the staff. Considering that I'm using a laptop, I decided just to use the battery. Strangely, the issue didn't happen: the temperature was fine. Two weeks later, they sent it back, noting me that they added more cooling gel to the GPU (I think it was cooling gel, it was something similar at least). I noticed the issue was slightly better, but still obtrusive. I eventually figured out that the issue only existed when the AC was present. Otherwise, the game ran fine.

Fast forward to this weekend: I buy Minecraft, a very basic 3D game (for anyone who has seen it, you know how simple the graphics are and how they should have little effect on performance). I play it, then I find that the issue still exists. So, that was the last straw: I install Ubuntu (which I've had only positive experiences with in the past) with the 'Restricted' nVidia drivers. Realizing that there was an included X Server configuration, I decide to launch it and monitor a single session of Minecraft. I suppose my computer decided that today was a good day, because it took about 10 minutes in order to heat up. But, alas, it did heat up. However, there was something strange I noticed about the settings: the driver was automatically overclocking the card! There are four possible configurations that the driver chooses from for the graphics, memory, and processor clock speeds. While playing the game, the driver chose the highest performance level (the one with the highest clocks).

Anyway, knowing all of that, I'll get to my question: is there any way that I can force the driver to use a specific clock speed, since it can obviously control it (keeping note that nvclock doesn't work with my card)? If not, is there anyway that I can force the fans to increase speed? Otherwise, is there *any* way to fix my issue? Thanks in advance!

Relevant information:
Graphics card: nVidia GeForce 9800M GTS
System Model: Gateway P-7811FX Gaming Laptop
Ubuntu Version: Ubuntu 10.10 "Maverick Meerkat" 64-bit (32-bit had the same issue)

---

### Post by pizza-is-good on 2010-11-03
Does it happen when you are in battery power?

Try disabling the nVidia driver. Does it still happen?

Try getting into your BIOS to see if there are any GPU overclocking options...

---

### Post by K25125 on 2010-11-03
> **pizza-is-good said:**
> Does it happen when you are in battery power?

Try disabling the nVidia driver. Does it still happen?

Try getting into your BIOS to see if there are any GPU overclocking options...

I found that it does not occur on battery power (the driver doesn't set the clock speeds to the highest values).

Since the game is Java, it requires OpenGL acceleration in order to run, but I tested it anyway. No dice. Is there some open source nVidia driver?

No overclocking, undervolting, fan control, or power management of any kind in my BIOS options.

---

### Post by K25125 on 2010-11-03
> **K25125 said:**
> I found that it does not occur on battery power (the driver doesn't set the clock speeds to the highest values).

Since the game is Java, it requires OpenGL acceleration in order to run, but I tested it anyway. No dice. Is there some open source nVidia driver?

No overclocking, undervolting, fan control, or power management of any kind in my BIOS options.

I found a way to force the driver to undervolt\underclock by editing the xorg configuration. For anyone who has the same issue, I used the guide here to force a clock speed on PowerMizer:
[https://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver#Force_Powermizer_performance_level_.28for_laptops.29](https://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver#Force_Powermizer_performance_level_.28for_laptops.29)

---

