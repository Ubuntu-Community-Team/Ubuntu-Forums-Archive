---
title: "Sound not working, faint crackling sound when playing music"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by k10chen on 2009-04-13
Hi guys

rather wierd problem

my sound is not working,whenever i play something that i know maks sounds, a faint crackling sound comes from my speakers.plugging in headphones provide no sounds either

strange thing is, this was working perfectly fine, i restarted my computer, and it stopped.

on windows, theres a way to uninstall the driver, and i was wondering if there is a way to do that on ubuntu as well


thanks

-K

---

### Post by eeeandrew on 2009-04-13
I've had similar problems myself in the past. First step is to determine which make of sound card you have. in terminal type> sudo lspciand look for an entry entitled "audio device" then do a search on the forums for the make of card you find. Hopefully there should be a good guide to fixing it. I'm sorry to say I'm not brilliant on the hardware side of things but that should get you started. If you post your card name back here hopefully someone should be able to help.

Hope this is useful,
Andrew

---

### Post by k10chen on 2009-04-13
solved it... browsed through the forums and it happened that one of the master volumes were set to mute... dont know how that happened...

---

