---
title: "flash player help?"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-03-28
here's my problem: (running xubuntu 8.04)

im playing a game on armorgames.com called last stand 2. and its just laggy. i tried a different game that runs on adobe flash player and its still laggy.
i tried clearing firefox cache but no help.
i have the latest version of firefox and adobe flash player installed.

i'm also running compiz fusion. i dont know if compiz is causing it to lag.
i also disabled adblock plus but no help.

pc specs: intel celeron 3.33ghz, intel GMA 950, 1 GB ram

any suggestions? thanks!

---

### Post by Therion on 2009-03-28
So you have the Adobe flash-plugin installed, correct?  If so then search in Synaptic for "Gnash".  

If you find you have Gnash installed, remove it; leaving the Adobe flash-plugin as the sole flash-handling plugin.

If still no joy, try using the Compiz-switch to turn off Compiz (and restart it just as easily) when playing Flash games and see if that's the issue.  I suspect it may be...

Compiz Switch:  [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by iam_newhere on 2009-03-28
> **Therion said:**
> So you have the Adobe flash-plugin installed, correct?  If so then search in Synaptic for "Gnash".  

If you find you have Gnash installed, remove it; leaving the Adobe flash-plugin as the sole flash-handling plugin.

If still no joy, try using the Compiz-switch to turn off Compiz (and restart it just as easily) when playing Flash games and see if that's the issue.  I suspect it may be...

Compiz Switch:  [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

tried switching compiz off. but unsuccessful. still laggy.
could you please try playing last stand 2  on armorgames.com? to see if its just me or its laggy for everybody.

---

### Post by Therion on 2009-03-28
I did.  Runs smoothly for me.  What about:  [http://www.albinoblacksheep.com/](http://www.albinoblacksheep.com/)   Can you play flash videos smoothly?

What version of Ubuntu are you using?  32 or 64 bit?  And how did you install your flash-plugin?

---

### Post by iam_newhere on 2009-03-28
> **Therion said:**
> I did.  Runs smoothly for me.  What about:  [http://www.albinoblacksheep.com/](http://www.albinoblacksheep.com/)   Can you play flash videos smoothly?

What version of Ubuntu are you using?  32 or 64 bit?  And how did you install your flash-plugin?

im using xubuntu8.04 32-bit

i installed flash when it asked to install the missing plugins.
then it took me to the adobe website.
i selected the version .deb for ubuntu 8.04++. and thats it installed it that way.

i can play videos smoothly though.. the games are just laggy.
the [http://www.albinoblacksheep.com/](http://www.albinoblacksheep.com/) isnt as laggy though. its pretty smooth.

did i do something wrong when i installed it?

---

### Post by carml on 2009-03-28
Did you check if there's Gnash installed? Before I had a "similar" problem with videos on Youtube,some were perfectly charged,some not and it wad due to a conflict between Gnash and Adobe Flash Player. I solved it removing Gnash, so try first this option. :)

---

### Post by iam_newhere on 2009-03-29
> **carml said:**
> Did you check if there's Gnash installed? Before I had a "similar" problem with videos on Youtube,some were perfectly charged,some not and it wad due to a conflict between Gnash and Adobe Flash Player. I solved it removing Gnash, so try first this option. :)

no i didnt have gnash installed. i already checked.
 what could be the problem?

---

### Post by carml on 2009-03-31
Maybe any games are in java? It's a shot in the dark,check if there some entry for java installed :confused:

---

### Post by iam_newhere on 2009-04-02
> **carml said:**
> Maybe any games are in java? It's a shot in the dark,check if there some entry for java installed :confused:

i think i got it working already. i reinstalled the whole system. lol

what i did was install adobe's flash player from the synaptic package manager. i think that did the trick. cuz the one in adobe's website was version 10. something. the one in the package manager was 9. something. 

so yeah. i think 9. something was more stable than 10. something for xubuntu.

---

### Post by KillerKael on 2009-07-22
I figured it's something to do with Adobe Flash Player 10. Unfortunately, I can't seem to get a version of Adobe Flash Player 9 from the synaptic anymore. Any suggestions?

---

### Post by KillerKael on 2009-07-23
iam_newhere, could you please tell me the exact version of Adobe Flash Player that you installed that worked? Thanks

---

