---
title: "Monitor, font, and other things."
date: 2009-10-11
forum: New to Ubuntu
---

### Post by AtariRaccoon on 2009-10-11
I have a few questions and issues with my nice little Ubuntu.

1.  I've already downloaded and installed the Microsoft Core fonts through the traditional add/remove application.  I'm wondering if I can move fonts in have installed on my windows partition onto my Ubuntu setup manually.  I found a few instructions on it here, including getting Nautilis to open via sudo to access the proper folders to past.  But after 'simply copy and pasting' the desired fonts and refreshing the font cache, the font only comes up as square blocks all over the screen (obviously it either can't read the font, or I messed up).  Of course, the font in question is Tahoma

2.  My picture alignment on my computer screen is a tad messed up when I boot Ubuntu.  I usually have to manually move the horizontal dispaly a bit of a deal to the left when I run Ubunto, and having to move it back to the right when I boot up windows.  Should I install my monitor drivers into Ubuntu, or does that have absolute nothing to do with anything?

3.  This is the kicker.  Whenever I have the Add/Remove Application open for more than just a few mintures (including the installation of a program), something decides to take a great deal of interest in my hard drive.  Weather installing something or not, it almost sounds like my hard drive is being defragged (basically a LOT of reading/writing going on) like there's no tomorrow.  This usually causes everything to just bog down and eventually to the point I can't even move the cursor on the screen.  Once I waited it out but after 30 mins, I could do nothing else but hit the reset button :(

I wonder what it's doing or causing it...


4. oh one more thing, any way I can get Ubuntu to STOP using my in-computer speaker so I can have some piece and quiet (and some apps actually USE that dang little speaker too, like Robots, but I got that to stop at least).  I like all my audio through my sound card, thank-you-very-much :P

---

### Post by yeats on 2009-10-11
> 1. I've already downloaded and installed the Microsoft Core fonts through the traditional add/remove application. I'm wondering if I can move fonts in have installed on my windows partition onto my Ubuntu setup manually. I found a few instructions on it here, including getting Nautilis to open via sudo to access the proper folders to past. But after 'simply copy and pasting' the desired fonts and refreshing the font cache, the font only comes up as square blocks all over the screen (obviously it either can't read the font, or I messed up). Of course, the font in question is Tahoma

You might take a look at this: [http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts/](http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts/)

> 3. This is the kicker. Whenever I have the Add/Remove Application open for more than just a few mintures (including the installation of a program), something decides to take a great deal of interest in my hard drive. Weather installing something or not, it almost sounds like my hard drive is being defragged (basically a LOT of reading/writing going on) like there's no tomorrow. This usually causes everything to just bog down and eventually to the point I can't even move the cursor on the screen. Once I waited it out but after 30 mins, I could do nothing else but hit the reset button 

Open a terminal window when this starts to happen and type:

```
top
```

This will open a program that shows your system load, memory usage, and the programs that are taking up the most resources at the top of the list.

Sorry - I don't have advice for you about the display issue. :-)

---

### Post by AtariRaccoon on 2009-10-12
As stated, I already have installed the Ms core fonts, I'm just greedy and want MOAR.  But I did see some links to other steps of manually moving fonts on over.

Ran top in terminal, and as luck would have it, I haven't experienced the problem yet while having the add/remove program running... so my other bet may be the power saver/screensaver? since I do remember the screensaver kicking in during a program installation.  Does Ubuntu do hard drive service and defragging during idle periods perhaps?

But one process that was being used a lot was Xorg... I wonder what that is....

---

### Post by achase79 on 2009-10-12
create a .fonts directory in your home and drop them in there.  This should pick them up.  For a multi-user way is to put them in /usr/share/fonts/truetype (this requires super-user privilages)

---

### Post by AtariRaccoon on 2009-10-14
Hee hee, I pretty much did the above method for moving my fonts on over and have actually moved them over.  Though oddly, they all work except for Tahoma, no real loss there though, it's all the others I wanted XD

I finally caught a hold of that hard drive I/O usage.  I immediate opened a terminal window to run TOP to see what was up, but before I could type, half of my terminal screen was flooded with:

^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ
^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ
^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ
^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ
^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ
^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ
^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ
^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ^[OQ<then the prompt here>

all while that dang PCM speaker kept beeping like crazy.

Any thoughts?

---

### Post by AtariRaccoon on 2009-10-15
I caught it doing it again but I was able to check the process running to see what was going on.  I caught this process being run:

update-apt-xapian-index

so it seems the OS is trying to actually update programs on the fly without my access to even push a button or even any kind of prompt.  So I can assume that going into the setting of the download manager and shutting down the automatic updater might do the trick?

---

### Post by nvikram on 2009-10-15
Hmm, you're update manager problem sound a bit weird, I have never experienced that one before. You're terminal though, are you sure there is no key being pressed, ususally a key press will cause a random character to show up and the pcspkr to start going.

For you're monitors, you might want to try System > Prefrences > Display.

Besides, top, check out System Monitor (System > Adminstration > System Monitor) I find it a lot more helpful (not to mention an actual GUI) for solving my solutions.

---

### Post by AtariRaccoon on 2009-10-15
Yeah, I find it weird too that update programs just start out of nowheres, especial WHILE I'm doing something.  I use top since I can access it quicker if the cpu is being bogged down but once I see something I do switch to the system monitor to get a better description.  I did a bit of research and found that ^[OQ is the terminal form of the F2 key, maybe a key got virtually stuck (which happens often I find).  Though odd I'd get the text spam BEFORE the command prompt though

Unfortunately for my monitor, there's no horizontal alignment settings in it, or that I noticed.  All it lists is the resolution and 'unknown monitor'.  I wonder if my driver CD has drivers that Ubuntu can install, or is there another process of installing proprietary drivers I don't know of yet. :P

Now if I can just get the OS to stop going beep-be-be-be-be-beeeep through that foolish PCM speaker when I shut down or reboot the OS.  I swear I'm gonna rip out that little wire connected to the speaker to end my suffering XD

---

