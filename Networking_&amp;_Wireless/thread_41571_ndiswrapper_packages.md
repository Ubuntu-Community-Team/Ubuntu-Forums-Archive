---
title: "ndiswrapper packages"
date: 2005-06-14
forum: Networking &amp; Wireless
---

### Post by Hobbes on 2005-06-14
Hello, I am a newbie to the max at linux, and while I had been running 5.04 fine for a few months at school, after coming home I had the pleasant surprise of everything breaking (ok well a couple things). After a bunch of research and a couple tries I figured out how to fix the resolution problem I was having from switching to a CRT 1600x1200 default to an LCD 1280x1024 default.

Now however, I have a problem because I am on a wireless connection here at home, and my linksys wifi adapter much to my delight doesn't have linux drivers. I looked into it, found ndiswrapper, looked good, but unfortunately I have no internet, so I can't use the usual synaptic/apt-get method to install it.  I tried d/l both the .deb package and source (from another computer) and transfering them, but I encountered some errors, I believe because I don't have other packages needed such as some sort of kernel development/build something or rather package.  I just need a list of everything ndiswrapper depends on and possibly some links to those packages to download. Thanks for your help.

---

### Post by kiddo on 2005-06-14
All you have to install is ndiswrapper-utils (version 0.12+1.0rc2-1), which depend on libc6 (version 2.3.2ds1-4 or higher) and perl (no version specified).

Don't you have a wired network so you can work on that linksys issue? I plugged a pcmcia xircom 10/100 card on mine so I could have all my time...


All this is considering you don't want to mess with compiling ndiswrapper 1.1thingy from the wiki tutorial. Pretty useless, the package from synaptic is older, but works fine (and it allows you to avoid messing it up at each kernel upgrade)

---

