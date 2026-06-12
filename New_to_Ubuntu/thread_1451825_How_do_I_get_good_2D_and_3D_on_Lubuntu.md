---
title: "How do I get good 2D and 3D on Lubuntu?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Azu on 2010-04-11
Hi

No matter what settings I use, the fglrx driver has bad 2D performance, and the radeon driver has bad 3D performance.

I've tried countless different versions of Lubuntu/Xorg/Mesa/Linux with fglrx (windows drag around slowly/tearing in videos/no KVM (slow desktop switching) etc) or radeon (only OpenGL2.0 (so even most games supported by WINE won't start), bad performance in ones that do).. and neither one will run new 3D engines that use DirectX 10 features at all.. have tried countless tweaks to more files than I can remember.. x86 and x64.. nothing gets good 2D and 3D, though. I heard VirtualBox used VT to provide DirectX support but it turned out all it did was run stuff in WINE using the host's video drivers..  defeating the whole point. Is there some hypervisor out there that I can install Windows on for 3D gaming and let me keep using the radeon driver in Ubuntu for everything else? My CPU supports VT-d which I read can be used to give direct hardware access, but I don't know what makes use of it properly.. please help, I'm at my wit's end here! I was thinking of trying VMWare but then I read it only supports DirectX 9, like WINE, and relies on the host OS having good 3D performance, like WINE. I saw some guy on YouTube apparently do it when Xen.. but everything I could find said Xen doesn't support this unless you have two monitors and GPUs (which I don't).


CPU: Nehalem
MB: x58
GPU: RV770


p.s.
Please forgive me if this has already been solved already. I honestly did search before asking.

p.p.s.
I don't care if the 3D stuff won't be able to run in a window on the Linux desktop, since it will be full screen anyways, so I have no problem if the solution requires Linux to completely give up my GPU while 3D stuff is running.

p.p.p.s
I tried to start a separate X session for 3D stuff with an xorg.conf saying to use the fglrx driver but that didn't work out either.. I couldn't even use reisub to shut down and nothing was logged in syslog or Xorg.0.log :/

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
[Found this]("http://ubuntuforums.org/showthread.php?t=878709") when I [googled this]("http://www.google.com/#hl=en&ei=5HPBS8rFB8KB8gav7YD9CA&sa=X&oi=spellfullpage&resnum=0&ct=result&cd=2&ved=0CAYQvwUoAQ&q=RV770+ubuntu&spell=1&fp=bcdf8cbbf06dc4f").

---

### Post by Azu on 2010-04-11
> **Sin@Sin-Sacrifice said:**
> [Found this]("http://ubuntuforums.org/showthread.php?t=878709") when I [googled this]("http://www.google.com/#hl=en&ei=5HPBS8rFB8KB8gav7YD9CA&sa=X&oi=spellfullpage&resnum=0&ct=result&cd=2&ved=0CAYQvwUoAQ&q=RV770+ubuntu&spell=1&fp=bcdf8cbbf06dc4f").

I already tried installing fglrx.

---

### Post by Perfect Storm on 2010-04-11
> How do I get good 2D and 3D on Lubuntu?

Switch the card to nvidia if possible.
In a couple years of time the Open ATI driver will properly (may)be as good as Nvidias.

Check the dicussion about here: [http://ubuntuforums.org/showthread.php?t=1388516](http://ubuntuforums.org/showthread.php?t=1388516)

Discussion about ATI open driver here (by member: Handy): [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by Azu on 2010-04-11
> **Artificial Intelligence said:**
> Switch the card to nvidia if possible.
In a couple years of time the Open ATI driver will properly (may)be as good as Nvidias.

Check the dicussion about here: [http://ubuntuforums.org/showthread.php?t=1388516](http://ubuntuforums.org/showthread.php?t=1388516)

Discussion about ATI open driver here (by member: Handy): [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

So if I buy a GT240 and use nVidia's driver I will have good 2D (LXDE/MPlayer/Firefox/Chromium) performance and also good 3D (like OGL3/DX9/DX10)?

I think I can make the money to buy one faster than waiting a couple years. I want to make sure we're on the same track here though because it would suck to waste the money and find out my problem still isn't solved.

I'd really prefer a solution that would work with my current harder, either way, though.

---

### Post by Perfect Storm on 2010-04-11
Aye, if you don't mind using closed source driver.

I myself uses nvidia gfx 285 1GB, works like charm with driver 195.

> I'd really prefer a solution that would work with my current harder, either way, though.
Then you have choose 1) good 2D (open source driver) or 2) decent 3D (close source driver)

---

### Post by Azu on 2010-04-11
> **Artificial Intelligence said:**
> Aye, if you don't mind using closed source driver.

I myself uses nvidia gfx 285 1GB, works like charm with driver 195.

Awesome, thanks. I thought I would need to get some kind of VM or hypervisor and install Windows.

Before I go out and buy one, though, could you give me a little info on how it works? Does their driver come with a special version of WINE, or..???
I hate not knowing how something works, even if it does work good. :confused:

---

### Post by Perfect Storm on 2010-04-11
Your system uses the driver, which allows you to run 3D games/stuff in wine (do also check wineHQ for ratings of specific game). I'm not sure how well Virtualbox supports 3D, you might give it a search, as I recall it it 3D via virtual is still experimental.


Do also check our wine forums for questions and answers.

---

### Post by Azu on 2010-04-11
> **Artificial Intelligence said:**
> Your system uses the driver, which allows you to run 3D games/stuff in wine (do also check wineHQ for ratings of specific game).
Oh.. so it will be like fglrx with good 2D? Not very good 3D, just DX9?

> **Artificial Intelligence said:**
> I'm not sure how well Virtualbox supports 3D, you might give it a search, as I recall it it 3D via virtual is still experimental.

Like I said, I tried it, but it just used WINE and the host drivers.. so not good 3D..

> **Artificial Intelligence said:**
> Do also check our wine forums for questions and answers.

I did search there (and elsewhere) before posting this.. I haven't found any way to get good 3D with it though. Just (glitchy) DX9.

---

### Post by Perfect Storm on 2010-04-11
> Oh.. so it will be like fglrx with good 2D? Not very good 3D, just DX9?

Yes, but the FPS, performance and quality a way better with the nvidia driver than the ATI close driver.

---

### Post by Azu on 2010-04-11
> **Artificial Intelligence said:**
> Yes, but the FPS, performance and quality a way better with the nvidia driver than the ATI close driver.

I was looking for a way to have good 2D performance like the radeon driver, but also good 3D performance like fglrx (better is fine too, but it is fast enough for me already) and working with more than just half of DX9.0.. I don't think it is good 3D if only things from half a decade ago or older will run.. :(

---

### Post by Perfect Storm on 2010-04-11
Sorry, I can't think of something else, other than wait for the Open ATI driver matures.

---

### Post by Azu on 2010-04-11
Thanks. I'll try to be more patient.


Update:
Actually the new version of Xen (4.0) only needs one GPU. It took a while to set it up with a hotkey for switching between dom0/domU and reinitializing video properly when I switched.. but all is well now. No waiting for WINE for me :D

---

