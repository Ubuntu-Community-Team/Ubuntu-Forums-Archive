---
title: "xserver question"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by erikyuu on 2009-08-09
Recently, I've been running some stuff that is resource intensive, making my system slow to a crawl. I've been thinking that if I bypass Gnome (resource hog that it is), I might be able to get a more usable system. In fact, if I can get rid of a DE overhead, that'd be great. 

I'm thinking my solution is using a pure xwindows/xterm session, as in whatever gui comes with the xserver since the program I'm running has a gui. Problem is I don't know how to work directly with the xserver, since pick-your-DE (gnome, in my case) does it for me, and am having a little bit of difficulty with the lingo so reading Xorg.wiki's FAQs doesn't help much.

I figure installing a lightweight DE like fluxbox or lxde is probably the least painful method, but...  There's a part of me that wants to see how much juice I can give to the app in question..

---

### Post by Bucky Ball on 2009-08-09
If you know the command to run it, stop your xserver and run it. You will find the instructions for stopping Gnome easy enough. 

You just hit ctl/alt/f1, stop GDM/xserver and issue the command to run your app. To start x, simply:

startx

---

