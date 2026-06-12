---
title: "[SOLVED] No Sounds in AMSN ubuntu 8.10"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by SILLAT on 2008-12-07
I'm running Ubuntu 8.10 on a desktop PC an i've trying to configure AMSN to hear sounds wen a new IM comes in  cuz wen i get a new message i dont hear nothing, can some someone send me there settings they use to get sounds out of AMSN or help me to get it to work .
i can play music like wise hear videos online and i'm using the default sound settings in ubuntu 8.10 dont kno if tellin u all this can get me help faster

---

### Post by zzHanks on 2008-12-11
I fixed this by changing the sound server (in Account > Preferences - Others tab) to "Use the Snack library (Tcl internal)"

If that does not work you can try "Use a different program" and type ```
aplay $sound
```Note: I'm running Hardy, but I hope this helps.

There's more info here: [http://ubuntuforums.org/showthread.php?p=3049953#post3049953](http://ubuntuforums.org/showthread.php?p=3049953#post3049953)

---

### Post by halitech on 2008-12-11
> **zzHanks said:**
> I fixed this by changing the sound server to "Use the Snack library (Tcl internal)"

If that does not work you can use a different program and type ```
aplay $sound
```

Note: I'm using Hardy, but I hope this helps.

I had to change mine to other program and for the code I used
```
play $sound
```

---

### Post by SILLAT on 2008-12-12
Hey Guys thnx for your input but it came a lil too late . .but thnx anyway
i did a lota a reading and struggled to find a fix for this , i tried alomst everything but in the end what i did was change my settings under preferences -> Other -> sound server to "paplay $sound sound"
and that did the trick . . .
thnx ya'll

---

