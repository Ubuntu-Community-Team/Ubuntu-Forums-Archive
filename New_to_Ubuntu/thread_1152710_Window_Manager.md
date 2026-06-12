---
title: "Window Manager?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by akakingess on 2009-05-08
I have been reading, and I liked the look and themes for IceWM, so I installed it, but when I tried to run it the terminal said another was already running, so do --replace. I also tried that and that seemed to lock up the terminal. What I am wondering is what is the default WM? - Compiz, because I also tried uninstalling that and IceWM still wouldn't work. I know the answer is out there and I did try, but I am at my wits end and doing a clean install of Jaunty just to be safe and start over. Any input/advice would be greatly appreciated. Thanks in advance.

Earl

---

### Post by mcduck on 2009-05-08
> **akakingess said:**
> I have been reading, and I liked the look and themes for IceWM, so I installed it, but when I tried to run it the terminal said another was already running, so do --replace. I also tried that and that seemed to lock up the terminal. What I am wondering is what is the default WM? - Compiz, because I also tried uninstalling that and IceWM still wouldn't work. I know the answer is out there and I did try, but I am at my wits end and doing a clean install of Jaunty just to be safe and start over. Any input/advice would be greatly appreciated. Thanks in advance.

Earl

If you want to try IceWM, you should select it at the login screen. Just click the session-button and pick IceWM from the list before typing your username & password.

By the way, the default window manager for Gnome is Metacity. But if you have desktop effects enabled you are using Compiz instead.

---

### Post by akakingess on 2009-05-08
That's IT?!? Thank you for explaining that, now I install IceWM and choose options before logging in and it will be on that list? If it is that simple, I shouldn't be allowed to fool around with this kind of stuff, but that's what us noobies are here for, right?  We were all noobies at some point in time!

Earl

---

### Post by neo.patrix on 2009-05-08
> I know the answer is out there and I did try, but I am at my wits end and doing a clean install of Jaunty just to be safe and start over.

You do not need to reinstall Jaunty for small thing like switching Windows Manager. Metacity and Compiz are stable enough; you can install more than one windows managers in parallel on same system. So there should be no need to remove Compiz for using IceWM

---

### Post by akakingess on 2009-05-08
I do that just because after I have done installing/uninstalling that may not have been neccessary, then I would just rather clean install, the stuff I need is all backed up and it doesn't take too long to reinstall Jaunty, so better safe than sorry is always my philosophy, but thanks for letting me know I probably didn't have to do it.

Earl

---

### Post by mcduck on 2009-05-08
> **akakingess said:**
> That's IT?!? Thank you for explaining that, now I install IceWM and choose options before logging in and it will be on that list? If it is that simple, I shouldn't be allowed to fool around with this kind of stuff, but that's what us noobies are here for, right?  We were all noobies at some point in time!

Earl

Yes, it should appear on the list of available sessions when installed. At least every window manager and DE I've tried does that.

Actually simple "icewm --replace" should work as well, but I've never used IceWM so I'm not quite sure how happy it would be running together with Gnome. Besides it has it's own panel and stuff so you'd probably want to run it as stand-alone window manager anyway.

---

### Post by akakingess on 2009-05-08
What is really sad, is that I got it running and after trying for about 10 minutes, decided that it was horrible and would take so much customizing just to make it tolerable, that I am back to square one. But I still love Gnome and Metacity, just would like to change the default # of workspaces available, or how to add more.

Earl

---

### Post by mcduck on 2009-05-08
> **akakingess said:**
> What is really sad, is that I got it running and after trying for about 10 minutes, decided that it was horrible and would take so much customizing just to make it tolerable, that I am back to square one. But I still love Gnome and Metacity, just would like to change the default # of workspaces available, or how to add more.

Earl

if you don't use desktop effects, right-click the Workspace Switcher-applet in your panel, select "Preferences" and you get a window where you can set the amount of virtual desktops.

If you use the desktop effects, install Compizconfig Settings Manager, and you'll find the amount of virtual desktops under general settings.

---

### Post by akakingess on 2009-05-08
Sweet, Thank you!!!

Earl

---

