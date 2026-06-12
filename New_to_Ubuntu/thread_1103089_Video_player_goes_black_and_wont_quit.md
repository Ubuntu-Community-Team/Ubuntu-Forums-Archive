---
title: "Video player goes black and wont quit"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by h_ryan503 on 2009-03-22
First off I'm very new to Linux and Ubuntu and open source in general.

Whenever I play a video no matter what player ( vlc, totem, mPlayer ) after just a few seconds it goes full screen and black. The audio will still play but the screen is black and no matter what I do the program wont quit.

I've tried all the shortcuts to make it stop I know, and I don't have access to anything since the screen is all black. It pretty much locks me out and I have to do a hard reset to exit.

At first I thought it was just avi files, but now its doing it with my DVD's, and anything else I try and play. I started vlc and had the errors sent to a text file and attached it. Let me know if there is anything you might need to know to try and fix it!

Thanks

---

### Post by stoogiebuncho on 2009-03-27
I can't really help you with your video problem, but I'll reply anyway to bump this back to the front page.

If a program freezes, there are a couple of things you can try before doing a hard boot.  First of all, if you assign a keyboard shortcut to your terminal, then you'll be able to access it even if a program is dominating your screen.  Once in the terminal, you can type 
```
xkill
```

Your cursor will change to an X symbol, and then next window you click on will be killed.

If that doesn't work, you can always force a log out by pressing Ctrl+Alt+Backspace.

Hopefully someone will be able to help you get to the root of your video problem.

---

### Post by h_ryan503 on 2009-03-27
Thank you so much! 

The xKill command works great. I didn't realize when I use the shortcut for the terminal it went into focus so I could enter a command. Video still doesn't play well, but at least I don't have to hard reset.

Thanks again

---

