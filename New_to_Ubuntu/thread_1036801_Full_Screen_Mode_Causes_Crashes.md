---
title: "Full Screen Mode Causes Crashes"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by urbandryad on 2009-01-11
I need help with a little problem. Well I'd say its a large problem. I cannot run any program in full screen mode (except for like, text based programs, like firefox and such.)

This problem mostly comes in with games, which start in full screen mode. It'll either cause the program to just crash. Cause my screen resolution to change and the program then to crash. Or else the program freezes, my OS freezes, and I have to force quit or restart.

This problem means that a lot of games I've downloaded won't even load because they load in full screen mode default. I can't play Supetux or Lincity-NC (though the 3D graphics may be at fault to)

But I was able to get Pingus to run by changing it to windowed mode. It was in a sort of buggy state before I switched it out.

My stats: Acer Extensa 4630z laptop, 1280x800 monitor. Intel Dual-Coer Pentium processor.

The graphics are: Integrated Intel GMA 4500M

More stats on this laptop here: [http://computershopper.com/laptops/reviews/acer-extensa-4630z](http://computershopper.com/laptops/reviews/acer-extensa-4630z)

This is the only problem I've found since putting Ubuntu on this computer. I guess I'm lucky. :3

---

### Post by urbandryad on 2009-01-11
Bump. Am I allowed to bump?

Please. Don't ignore me. I would like to play games and use fullscreen mode, thanks.

---

### Post by RomeReactor on 2009-01-11
Hi. It's strongly recommended that you wait at least 24 hours before bumping your thread; even if it looks like no one knows the answer to your particular problem, give people a chance to respond to your post.

I don't have experience with Intel video cards, but try this from a terminal to see if you have the drivers correctly set up:
```
glxinfo | grep rendering
```
and post the output. Also run this:
```
glxgears
```
If you see a window with gears spinning, you have direct rendering enabled and the problem is likely elsewhere.

---

### Post by urbandryad on 2009-01-12
This is what I get. Used asterisks to hide my name.


********@********-laptop:~$ glxinfo | grep rendering
direct rendering: Yes
********@********-laptop:~$ glxgears
3250 frames in 5.0 seconds = 649.909 FPS
3442 frames in 5.0 seconds = 688.342 FPS

---

### Post by RomeReactor on 2009-01-12
Make sure that the games are running in a fullscreen resolution lower than the resolution of the laptop's display. Try running the games from the terminal (usually it's the name of the game's executable) and post the output; maybe we can find out what the problem is. Also, if you installed the games from the repositories, they should have a manual accessed by writing **man** (for 'manual') in the terminal, followed by the executable. You can find options there to force most games to start windowed.

---

