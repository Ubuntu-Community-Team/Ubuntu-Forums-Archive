---
title: "periodic freezing"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by volatilesquirrel on 2009-03-24
i installed ubuntu yesterday and it seems to be running great with the exception of complete system freezes every 2 to 5 hours.  i really am not sure how to begin going about troubleshooting this problem, any advice?

---

### Post by woppy71 on 2009-03-24
I wonder if this could have anything do with hardware stability?

Is there anything in particular that you do just before it freezes?

What sort of things are you doing with the system?

Hmmmm... any info on errors or symptoms would be helpfull :)

---

### Post by jakupl on 2009-03-24
Is it possible to hit (ctrl + alt+ F2) to get you to a virtual terminal? 
Try this, log in and write
```
top
```
then maybe you will see something that takes all your cpu.

But I doubt that is the problem

---

### Post by volatilesquirrel on 2009-03-24
well, i don't see how the top command in the virtual terminal will really help unless i stare at the screen for hours to see if it'll decide to freeze again ... also, how do i exit the virtual terminal?  i couldn't figure it out and just had to ctrl-alt delete to restart.

as for what are the conditions when it freezes, it's always completely random.  once while navigating the main menu, once while on the net and once while trying out freeciv.

***edit***

i should note: every incidence but one (the most recent which happened about five minutes ago) the mouse is still movable.  in this most recent occurrence the mouse froze along with the screen.

---

### Post by jakupl on 2009-03-24
> **volatilesquirrel said:**
>  also, how do i exit the virtual terminal?  i couldn't figure it out and just had to ctrl-alt delete to restart.


ctrl + alt + F7

---

### Post by woppy71 on 2009-03-24
Ok, one of the first things to do would be to check the inside of the case, and give it a good old clean out (if there is a lot of dust) and pay particular attention to dust accumulation around heat sinks and fans. Give them a gentle brush with a small paint brush or similar and use a vacuum to get rid of any resulting dust. Needless to say, be gentle!

Also, carefully check to see if any expansion cards are correctly seated in their slots, you'd be suprised how often they can work loose, like wise, check all cabling to see that it is still firmly in-place.

Whilst you have the case panels off, just fire up the machine and check that any fans are spinning freely. If all is ok, replace panels and test the system again for stability.

If this dosn't work, then another, very common cause of random system lockups can be a symptom of a memory module failing, the way to check this is to boot with your Ubuntu cd and select the memtest option, and let it make at least 5 passes and check to see if it reports any errors.

Hope things work out! :)

---

### Post by volatilesquirrel on 2009-03-26
well, i opened the machine up and cleaned out all the dust on the components and fan.  I'm running a dell inspiron 6000 laptop and so i haven't gotten around to doing that in it's five year life.  i'm glad you suggested it because the machine is actually running faster and it doesn't overheat any longer if i forget it on for too long.

i also ran the memory test at least seven runs through and it came back clean.

unfortunately, i am still getting freeze ups.  here is a brief summery of the various freezes that i remember and have recorded:

* twice while accessing the main menu
* once while switching between firefox and exaile (audio player)
* once while playing freeciv
* once while opening a new tab in firefox (using middle mouse button)
* and once after inserting the ubuntu disk and then navigating though the menu to restart

with all of these freezes except the last i have retained control over the mouse and music has continued to play but doesn't advance to the next track once the current is over.

anymore light that could be shed onto this issue would be greatly appreciated

---

### Post by volatilesquirrel on 2009-03-26
i'd also like to add that, for whatever reason, it has been freezing up once every 20 minutes or so.  it definitely happens whenever i try to execute a task (such as opening a menu, application, document, opening new tab in firefox).  i'd really love to get this problem figured out because i'd hate to have to revert back to windows.

---

