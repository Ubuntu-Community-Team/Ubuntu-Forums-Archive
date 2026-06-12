---
title: "laptop spacebar doesn't work"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by newbie16301 on 2010-04-14
My laptop (integrated keyboard) spacebar suddenly stopped working.  Well, to be honest, it was after the cat threw up on the computer.  But all the other keys are working.  It seems to be something inside the computer, as I tried to do Control+C to copy a space so I could at least use Control+V when I desperately needed one, and while I can copy other letters, I don't seem to be able to copy a space.  I took the cover off and cleaned, but pressed everything and still no space.  Any suggestions?

---

### Post by hackb0y294 on 2010-04-14
Try prying the spacebar off and pressing the rubber keys under it. If it works then, you probably have the spacebar on wrong. If this doesn't work, you'll have to take the whole keyboard apart (check online for documentation) and check for something between the rubber key and the flat transparent plastic with dark looking circles (try pressing the dark circles with the tip of a pencil, if this doesn't work, your keyboard is probably broken).

Sorry if this is hard to understand, send me a message if you need more info.

---

### Post by undecim on 2010-04-14
A few things I can suggest:

If you can't get it working, but are confortable in partitally disassmbling your laptop, buy a new keyboard and put it in.

If that's not an option, the in most Ubuntu applications, you can press Ctrl+Shift+U, type "20" and press enter to generate a space (I use this trick a lot with "9" to make a tab on the forums)

And also, if you prefer the Copy/paste workaround, you might find parcellite handy. It keeps track of your keyboard history, even after a reboot, so you can still copy/paste other things and go back to the space.

If you have to compose a long message, you might also type it in gedit using tab to make a space, then press Ctrl+Shift+H and replace "\t" (tab) with " " (using the Ctrl+Shift+U or copy/paste trick)

---

### Post by msrinath80 on 2010-04-14
OR, you could always remap one of the extra keys to a spacebar. For example the right shift key. Find the keycodes for the spacebar press and release events and map them to the right shift key. Google for "Xmodmap remap keys". Good Luck!

---

### Post by lavinog on 2010-04-14
What model laptop is it.  I have found that laptop keyboards can be replaced pretty cheap.  You can sometimes find replacements on ebay for $10.

---

### Post by codemaniac on 2010-04-14
> you can press Ctrl+Shift+U, type "20" and press enter to generate a space (I use this trick a lot with "9" to make a tab on the forums)

that is pretty awesome.I am on my mysql prompt and it works here too..Can you please elaborate some of its other options too.Thanks..

---

### Post by newbie16301 on 2010-04-14
the laptop is a six-year-old IBM ThinkPad.  The cat has taken to sitting on it a lot, and presses multiple keys for long periods of time.  she reprogrammed it, so that the left side was normal but the right side was all numbers on every line.  that was fixed with the shift-numlock fix.  But that did nothing for this.  I tried cleaning it and tried pressing everything on the space when I had the cap off, but nothing worked.  I REALLY appreciate all the suggestions.  The cut+paste seems to work in typing and in the regular google search, but not in the little google serch bar I have on my toolbar.  I will try all the suggestions and get back with which ones worked for me.  I am not sure I am comfortable replacing the keyboard.  Maybe I could just plug in a new one if I am going to type a lot?

---

### Post by lavinog on 2010-04-14
> **newbie16301 said:**
> I am not sure I am comfortable replacing the keyboard.  Maybe I could just plug in a new one if I am going to type a lot?

here are some removal instructions for a thinkpad T40:
[http://www-307.ibm.com/pc/support/site.wss/MIGR-46515.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-46515.html)
You remove 3 screws and pop the keyboard out.

---

### Post by gnaag on 2010-04-15
It.is.no.the.problem.of.keyoard..Same.time.ubuntu.lucid.update.brokes.spacebar.and.my.wireless.mouse..Please.help..

---

### Post by scottuss on 2010-04-15
ihavethesameproblem.hasanyonefoundasolution?

---

### Post by lavinog on 2010-04-15
> **gnaag said:**
> It.is.no.the.problem.of.keyoard..Same.time.ubuntu.lucid.update.brokes.spacebar.and.my.wireless.mouse..Please.help..

boot into the live cd, if the spacebar doesn't work in the live cd, then it is your keyboard.

---

### Post by gnaag on 2010-04-15
I reinstalled all xkb and xkbv packages, restarted system and now it works

---

### Post by gnaag on 2010-04-15
> **lavinog said:**
> boot into the live cd, if the spacebar doesn't work in the live cd, then it is your keyboard.

It.sometimes.work.sometimes.do.not..In.shell.ctrlaltF1.it.works.well..There.is.some.problem.with.latest.updates.I.cannot.trace.the.reason.

Please.Help.It.urgent

---

### Post by lavinog on 2010-04-16
Does it work with a karmic live cd?  If it doesn't then you can rule out an update issue.

---

### Post by gnaag on 2010-04-16
Yes, it does work in live CD

---

### Post by lavinog on 2010-04-16
> **gnaag said:**
> Yes, it does work in live CD

I would suggest starting a new thread for your issue then.

---

### Post by Quanj on 2012-06-20
I have the same problem afetr a minor wine spill - just the spacebar not working. Went down the external keyboard route with a tried and tested keyboard, including tested on a.n.other laptop and - you got it - worked perfectly except for the spacebar. Any further suggestions - please?

---

### Post by lisati on 2012-06-20
> **Quanj said:**
> I have the same problem afetr a minor wine spill - just the spacebar not working. Went down the external keyboard route with a tried and tested keyboard, including tested on a.n.other laptop and - you got it - worked perfectly except for the spacebar. Any further suggestions - please?

Thread closed.
A lot can change in the space of two years. Sometimes it's a good idea to start a new thread so that things don't get confusing when something has changed.

---

