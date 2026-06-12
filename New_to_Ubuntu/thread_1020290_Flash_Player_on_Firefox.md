---
title: "Flash Player on Firefox"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by EMABrad on 2008-12-24
So I just got 8.04, and booted up Firefox, and it didn't have Flash Player.  I tried playing a video or something, and it brought me to the plugins for Firefox.  I was given a list of three different Flash players to choose from, so I picked the official Adobe one.  Firefox did everything and installed it for me.  It didn't work.  So I did the next one on the list, and that one does weird things.  Like, it has a big play button to click before it activates the Flash, which is annoying, and it screws around with proportions and colors, and I'm wanting to go to one that's not going to screw around like that.

Help?

---

### Post by igknighted on 2008-12-24
> **EMABrad said:**
> So I just got 8.04, and booted up Firefox, and it didn't have Flash Player.  I tried playing a video or something, and it brought me to the plugins for Firefox.  I was given a list of three different Flash players to choose from, so I picked the official Adobe one.  Firefox did everything and installed it for me.  It didn't work.  So I did the next one on the list, and that one does weird things.  Like, it has a big play button to click before it activates the Flash, which is annoying, and it screws around with proportions and colors, and I'm wanting to go to one that's not going to screw around like that.

Help?

What version of ubuntu do you have?

---

### Post by EMABrad on 2008-12-24
8.04.

---

### Post by igknighted on 2008-12-24
> **EMABrad said:**
> 8.04.

no, sorry i meant i386 or x86_64

---

### Post by EMABrad on 2008-12-24
Well, probably the first one, because I'm running on an older computer.

---

### Post by Strongman332 on 2008-12-24
my mother has the same problem in her hardy install but my hardy install does not, i can not find a plausible cause.

---

### Post by igknighted on 2008-12-24
What does it say in firefox tools->add ons->plugins?  Is flash listed?

---

### Post by Liviu-Theodor on 2008-12-24
Firefox needs restarting after installing Flash plugin. Have you done that (close browser, open it again)?

---

### Post by -kg- on 2008-12-24
I just checked in my Synaptics Pkg Manager ("System/Admin/Synaptics").  Flash runs on my system, and I found that I had none other than the "non-free" plugin installed.  All the others to do with Flash were not installed.

You'll need to make sure that you have all the Repositories enabled.  [Click here]("https://help.ubuntu.com/community/Repositories/Ubuntu") to access the page that tells you how to enable the Repositories.  You'll want to go ahead and click all the boxes.  Once you reload the Repositories, you should have access to the non-free version of the Adobe Flash Player.

Install that, and it *should* work.  I won't guarantee anything...it's just that flash player works for me on my system and this is what I show as installed.

---

### Post by EMABrad on 2008-12-24
Well, I have done as you have said above with the Synaptic Package Manager and removed the plugin, and Flash integrates perfectly.

... But with no sound.

---

