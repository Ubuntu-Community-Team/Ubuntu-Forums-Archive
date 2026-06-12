---
title: "Flash lags"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by completely new on 2010-06-26
I have ubuntu 10.04. I'm staring to hate ubuntu because this is one in the series of DOZENS of things that don't work properly, but I won't rant about that right now... Flash lags, when watching ordinary videos it usually doesn't, but HD videos and flash games are especially a problem. I tried a few fixes I found by googling, but nothing worked. Please help me with making flash work without lag, thank you.

---

### Post by sandyd on 2010-06-26
> **completely new said:**
> I have ubuntu 10.04. I'm staring to hate ubuntu because this is one in the series of DOZENS of things that don't work properly, but I won't rant about that right now... Flash lags, when watching ordinary videos it usually doesn't, but HD videos and flash games are especially a problem. I tried a few fixes I found by googling, but nothing worked. Please help me with making flash work without lag, thank you.
you using 64-bit ubuntu?
if you are, we can't help with the lag. Adobe pulled back support for x64 flash, which had no lag, due to a security issue. You are now running the 32-bit flash on a 64-bit system through a plugin called nspluginwrapper. The lag is normal for nspluginwrapper, because the hardware acceleration doesn't really work.

Since flash player is not open source software, we cannot improve on flash at all, but must rely on adobe to produce some form of working flash plugin for linux. Flash has always been a bit finky on linux anyways..

---

### Post by completely new on 2010-06-26
No, I'm using the 32-bit ubuntu.

---

### Post by sandyd on 2010-06-26
> **completely new said:**
> No, I'm using the 32-bit ubuntu.
Then see [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by completely new on 2010-06-28
> **carlee said:**
> Then see [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
Nope, that didn't help. It still lags.

---

### Post by philinux on 2010-06-28
> **completely new said:**
> I have ubuntu 10.04. I'm staring to hate ubuntu because this is one in the series of DOZENS of things that don't work properly, but I won't rant about that right now... Flash lags, when watching ordinary videos it usually doesn't, but HD videos and flash games are especially a problem. I tried a few fixes I found by googling, but nothing worked. Please help me with making flash work without lag, thank you.

System specs, graphics card?

Also try this.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by completely new on 2010-06-30
> **philinux said:**
> System specs, graphics card?

Also try this.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
That didn't help either. I'm getting really pissed.

There's nothing wrong with my pc and flash worked normally in windows. I have 512 mb asus radeon ah 2600 pro, 2,6ghz processor, 1,25gb ram.

I checked the processor and it's between 98-100% when a video on youtube is being played, when it's paused it's 50-60%, and when there's no flash around and firefox is running it's 30-40% and when I turn off firefox it's 20-30%. Maybe I should check the temperature, what's a good program for that?

---

### Post by Jakiejake on 2010-06-30
By The Way do you notice how nice the Ubuntu community is!

---

### Post by Johnsen9000 on 2011-05-22
i fixed it. i had the same problem, and i fixed it. so, windows lover, here is what you do:
install _[U]Flash aid_[/U][HTML]https://addons.mozilla.org/en-US/firefox/addon/flash-aid/[/HTML]uninstall adobe flash through ubuntu software.
restart firefox.
go to youtube or another flash-player place.
start a film. an error will occure, but then click on the flash aid button next to the google search window. 
press execute.
im not sure if it installs adobe flash or not, but it doesn't lag when you watch the flash in big screen.

---

