---
title: "Amarok and flac?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by cptrohn on 2009-05-31
Seems I am having some issues with amarok playing flac files?  I can play the files in both Rythmbox and Songbird... so I guess it's not REALLY a problem per se..... But was just wondering if amarok has issues with flac?


Has anybody else run into this problem?   Just for some more information, I had some of my music collection ripped into WMA... (with a high bit rate), and I recently used soundconverter and put them into flac and amarok crashes anytime I try to play those files.....It might be just those files that have been converted though as I've ripped some other stuff into flac but didn't try it again with amarok after it crashed with several different "experiments" with several of the converted files......  but as I said it seems to only be an amarok issue as I could play them no problems with songbird, rhythmbox, VLC etc...

---

### Post by durand on 2009-06-04
Amarok is a QT app while those others are GTK. They use different media engines so even if it works on one app doesn't mean that it will work on another. It's been a while since I used amarok so some vague instructions: in it's preferences, try changing it's sound engine to gstreamer.

---

