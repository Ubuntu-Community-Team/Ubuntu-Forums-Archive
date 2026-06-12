---
title: "Compiz stopped working right"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by shanep-server on 2010-10-31
Ok I had compiz all pimped out finally. I had the cube running on dual x servers... 2 22" lcd's each had its own cube. Then compiz started messing up... I switched drivers from restricted driver 195.xxxx Nvidia to Nvidia 260.19.12 

Now I can get too custom visual effects however when I try to enable the cube i'm getting problems. It doesn't work. I used to have reflection running as well.. which nolonger works... it stopped working before i changed my nvidia drivers.

When I try to enable reflection... it chops my borders of windows off.. like no top bar on windows.. or buttons to close minimize exand.... Also when I try to enable the cube... it mess's up my desktop something fierce but only on 1 of the 2 lcd x servers. The top panel turns transparent with no buttons... I can't do anything with the display... until it reverts back to normal. If it glitches out I can go to the other lcd an shut down linux but It doesn't even show the shut down or restart option I just have to hit enter and it shuts down... like the buttons are there they just are no longer visible. So the question is... why is the cube messing up like this all of the sudden and how do I get it back to working order...

If all else fails would I be able to just reinstall compiz manager or is that only a gui to something else that is messed up... is there a way to reinstall compiz if that is infact the problem?

Any ideas or suggestions would be awesome!

---

### Post by hyperdude111 on 2010-10-31
You can re-install compiz through synaptic

And im not sure if this will work but..when I have issues with compiz rendering things incorrectly this commands usually helps.

Press Alt-F2 and try 
```
compiz --replace
```

dont run it in terminal.

---

### Post by cpmman on 2010-10-31
I had a compiz problem and followed this advice which corrected it:-

***_[http://ubuntuforums.org/showpost.php?p=9964610&postcount=2](http://ubuntuforums.org/showpost.php?p=9964610&postcount=2")_***

---

### Post by trikster_x on 2010-10-31
Put this in a terminal:
```
compiz --version
```
If your version is higher than 0.8.6, then cpmman's post is the way to go.  The newer versions of compiz are highly unstable on 10.10.

---

### Post by theozzlives on 2010-10-31
I'd say switch your drivers back the way they were.

---

### Post by shanep-server on 2010-10-31
No it was doing this before I switched my drivers. I figured while it was messed up I had time to work on updating drivers. Its gotta be compiz no question.

---

### Post by shanep-server on 2010-10-31
Ok well I tried both references in this thread... they did not work. I finally uninstalled simple-ccsm then played with compiz settings... I got cube and rotate to work. However I couldn't zoom from the cube but it was present.. then I reinstalled simple-ccsm and it wouldn't work till i rebooted. Then everything worked good as new.

---

