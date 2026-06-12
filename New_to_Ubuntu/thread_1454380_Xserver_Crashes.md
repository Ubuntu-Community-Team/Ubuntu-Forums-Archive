---
title: "Xserver Crashes?"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by sleepwalka26 on 2010-04-14
**_Back Story:_**
     I recently upgraded to Kubuntu 9.10 after having no problems using Ubuntu 9.04 on my _[HP DV8225NR]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&product=1841885&dlc=en&docname=c00612970")_ laptop. After some unforeseen events the laptops 17" screen began to stop working how ever everything else worked perfectly(The laptop will boot up, however I cannot see anything displayed on the screen as if it is closed, i found that pressing a small button that tells the laptop the screen is closed, brings the screen back on for a few seconds then back to black. Now it does nothing at all. Also I can see a small crack in the plastic where the screen hinges and have found this to be a large defect in HP laptops). Basically turning my laptop into a desktop PC and me being strapped for cash I took an extra monitor we had laying around and am now using it for my main monitor. 
**_[COLOR="Red"]Problem:[/COLOR]_**
     While using 9.04 with the current setup (external monitor as primary monitor for laptop) I had no problems. However after switching to Kubuntu 9.10 Randomly the external monitor goes black as if it the computer is sleeping however I can still type and if there is any media playing i can still hear it. the only ways to get around it is to use a shortcut I made to open a terminal and restart my laptop that way or wait it out and then move my mouse or type a key and it usually comes back. Getting to the question: Is there any sort of script or bug or glitch anyone knows about that will help to patch this? or am I screwed till I can get a new pc?:confused:

---

### Post by sleepwalka26 on 2010-04-19
Bump

---

### Post by ibuclaw on 2010-04-19
What button do you press to tell the laptop screen is closed? Running xev from a terminal and pressing it should output the keycode for it.

And is it only 9.10 that has this defect? (ie: have no issues when booting into 9.04 LiveCD).

Regards

---

### Post by sleepwalka26 on 2010-04-20
I tried using xev and the button only seems to effect the laptop screen. I also tried a Ubuntu 9.10 live dvd that i had from the ubuntu book i bought. and the screen still went black at a random time. I have no clue what could be causing it i check the cord and have even unplugged then replugged the cord and still nothing. Windows the external monitor works just fine no black outs or anything. Ne Ideas?

---

