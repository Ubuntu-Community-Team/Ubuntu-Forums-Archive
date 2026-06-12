---
title: "wine sound acer aspire"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by chrisblack on 2009-01-09
I've been happy as a pig in muck for the last week... I got an Aspire (8gb SSD version), dumped Linpus and installed 8.10 immediately with no problems (thanks to the handy Ubuntu install guide)...

I've now hit my first problem..

I play a lot of music and use abc software... i tried using abc2ps etc... but am not too comfortable with command line stuff, preferring a GUI, so i installed Wine and my old favourite ABC Navigator...

ABC Navigator works fine under Wine, displaying music etc... however I can't get the sound to work, to listen to the tunes I have in ABC format..

Anyone give any pointers.. i've tried all the settings under Wine configuration/audio, but not so much as a beep...

Thanks

Chris

---

### Post by kostkon on 2009-01-09
Which version of *Wine* do you have? If you have installed it from the repos, then you have 1.0.1 which does not work with *PulseAudio*.

You need to install the latest version (1.1.12) that works well. Go [here]("http://www.winehq.org/download/deb") for instructions on how to add the official *Wine* repo.

After adding it you'll get an update notification for *Wine* to update it to the latest version.

---

### Post by chrisblack on 2009-01-09
Thanks - now got wine 1.1.12 -but still no sound from it... any more suggestions please?

did i need to install any other windows software?

Chris

---

### Post by finfin on 2010-12-12
Hi
I'm running Wine 1.3.9 and can't get sound from Abcnavigator
All else is seems okay running the program but it's a pain having a midi panel, watching it play but not being able to hear anything!

I'm guessing there has been no solution to this to date but if anyone can spare the time to look into it, I for one would be very grateful. There's such a paucity of GUI-based Linux progs that work with abc notation and being a linux-newbie I've struggled (and failed) to get anything up and running that requires anything but the simplest setup - and there seems nothing in this zone for abc. 

Musescore is great but it crashes on abc imports if it can't cope with the coding - at least it does for me.


Many thanks in advance
Fin

---

### Post by finfin on 2010-12-12
> **finfin said:**
> Hi
I'm running Wine 1.3.9 and can't get sound from Abcnavigator
All else is seems okay running the program but it's a pain having a midi panel, watching it play but not being able to hear anything! ... Fin

It's a tad embarrassing to reply so soon to say I've now got sound in abcnavigator via Wine after several weeks of being completely flummoxed by the no-sound problem. I really hope this fix turns out to work for others having this problem...

I found that my copy of abcnavigator was set (by default??) to use HARMONICA in the patch bank ; soon as I clicked on any one of the other instruments (just click on the 'patch' button to the left of the 'Pitch' wheel on the midi panel) voila....sound!! I've no idea why Harmonica produces no sound and the others do (I haven't been through them all but most of the one's I've clicked on so far work for me) :D

So, as far as my own scenario is concerned, the problem is solved. Hope this turns out to be an easy solution for others with the same issue.

Cheers
Fin

---

