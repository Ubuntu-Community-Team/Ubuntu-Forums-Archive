---
title: "Fastest, lightest, full browser for Linux"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by mattbutsko on 2011-04-26
Hey everybody, I've been using Ubuntu/Kubuntu/Linux Mint/Debian for a while now, and something I noticed, is that my browser performance is always very bad.

I've tried Midori, Opera 11 (I use this on stupid Windows), Firefox 4, Chrome, and Epiphany. I've got a quad core i7 that can clock up to 2.93Ghz on each core when need be. I have 4GB of 1333Mhz DDR3. nVidia 425M 1GB with proper drivers installed - ones that don't purple screen crash were hard to find - but not impossible.

Anyway, point is, what browsers are y'all using? The loading speed isn't an issue, it's the rendering and panning speed. Pages take 4 or 5 seconds to render after it's been downloaded, and after that, they scroll at like 14 FPS, and they lag behind my scroll wheel. Now, I do enable smoothscrolling via a Chrome/Chromium extension and a Firefox extension, both run great on Windows. I also enable Opera smooth scrolling since it's turned off by default on their Linux build.

Again, these extensions work great on Windows, and with my specs, there's no reason they shouldn't run great here.

Now, my machines a gaming rig for the most part, and I use Linux for web browsing/multimedia. If I can't find a browser that runs good enough, I'm going to have to drop Linux.

Anyone have any solutions?

---

### Post by K_45 on 2011-04-26
```
sudo apt-get install lynx
```

```
lynx
```

In seriousness, try FIrefox in safe-mode without any add-ons.

---

### Post by mattbutsko on 2011-04-26
Ah, that was pretty funny, but through all my research in my quest to find out why my web browsing sucks hard, I've learned all about Lynx.

Firefox in safe mode doesn't make a difference.

---

### Post by K_45 on 2011-04-26
Can you enter 

```
top
```

at the terminal and then browse. Are there any sites that begin to push your CPU or other resources up?

---

### Post by mattbutsko on 2011-04-26
Good idea, I tried a few browsers on a few sites, and so far I only hit 80% on heavy sites, so it's not really being pushed too hard.

Don't worry about it though, I installed an extension for FF called Grab and Drag, and it lets you pan a web page like an PDF, by grabbing it with the mouse. After finetuning it to my preferred settings, it scrolls at 55 to 60 FPS and Firefox 4 is decent enough at rendering speeds that I can get passed that.

This'll work for now.

---

### Post by K_45 on 2011-04-26
Hmmm, then mark this thread solved with thread tools. You could also check Nvidia's refresh rate settings which may or may not have something (or nothing) to do with this.

---

### Post by mattbutsko on 2011-04-26
Yeah I was about to, my bad, been trying to help some other guy with his touch pad issues.

---

