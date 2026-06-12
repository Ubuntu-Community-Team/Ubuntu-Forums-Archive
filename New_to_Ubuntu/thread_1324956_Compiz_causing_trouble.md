---
title: "Compiz causing trouble"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by synicalx on 2009-11-13
I was tinkering with my Compiz settings and I changed the window effects to "Blur" rather than "Wobble", then when I went to close that window everything locked up and it hung like that for 10 or so seconds, then the screen went black and all I could see was the outlines of my top and bottom task bars. Strangely enough behind all that it seems as if everything else was still working as when I hit my terminal shortcut (ctrl-alt-t for anyone interested :)) my HDD indicator flashed a bit showing that it was working!

Of course I did a hard shutdown (nothing else open besides compiz) and fired it back up again and the same thing happens. I can see the Ubuntu logo and loading screen, then the taskbar outlines then nothing.

I'm guessing the easiest fix would be to boot with default settings, but I can't seem to find a way to do that on the interwebs - any pros got a suggestion?

Btw, specs are - Ubuntu 9.04 running on an MSI Wind U100 from a clean install - no other OS at all

---

### Post by coldReactive on 2009-11-13
It would've been nice to tell us you have Intel 950 GM.

I ran Intel 945GM a while back on my Gateway laptop. Don't use blur, it won't work. That said, ALT+F2 and run metacity --replace to get rid of compiz for the time being if you can, then run ccsm and disable blur. re-run compiz see if that fixes everything.

---

### Post by synicalx on 2009-11-13
> **coldReactive said:**
> It would've been nice to tell us you have Intel 950 GM.

I ran Intel 945GM a while back on my Gateway laptop. Don't use blur, it won't work. That said, ALT+F2 and run metacity --replace to get rid of compiz for the time being if you can, then run ccsm and disable blur. re-run compiz see if that fixes everything.

Thanks for the reply, but how do I do that?

---

### Post by coldReactive on 2009-11-13
> **synicalx said:**
> Thanks for the reply, but how do I do that?

ALT+F2 should bring up the run command dialog.

In the text box, type in metacity --replace

then hit enter/OK. compiz should be replaced with the normal un-composited metacity window manager. From there, you can go into compizconfig settings manager (if it's installed, it will be in System > Preferences. If not, go to software center or add/remove and search for ccsm. If you have add/remove, then you need to select all available applications from the dropdown menu.)

---

### Post by synicalx on 2009-11-13
After typing metacity --replace I get "Window manager error: Unable to open X display"...

---

### Post by coldReactive on 2009-11-13
> **synicalx said:**
> After typing metacity --replace I get "Window manager error: Unable to open X display"...

Then you did something nasty. Did you by any chance install any drivers from synaptic that you shouldn't have?

---

### Post by synicalx on 2009-11-13
> **coldReactive said:**
> Then you did something nasty. Did you by any chance install any drivers from synaptic that you shouldn't have?


No, fired up Synaptic once to get Compiz from memory :D

Ah well, fresh install I'm guessing?


EDIT:

After all that, I went to boot from a USB 9.04 then for some odd reason it booted by default into my original Ubuntu install but with a different appearance profile loaded!

I'm at a loss as to why it did that, but something must have worked! Thanks!

---

