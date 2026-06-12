---
title: "Sticking Firefox and Compiz not working"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by wh1pla5h on 2009-01-07
Now I don't know if Compiz is the cause of this, but all of a sudden my firefox is sticking itself to my top panel and covering it so I can't get to the home menu. I know others have had problems with this, but I haven't found a solution to it. Compiz is also not working even though I boot it up and reload the manager none of its effects are working. Is there a way to return Ubuntu to its default settings?

---

### Post by adult swim on 2009-01-07
when firefox messes up like that try hitting f11 two times
some people have reported a permanent fix that is that after they hit f11 two times, then they click the restore window button (the one between minimize and maximize) and then restart firefox.

---

### Post by wh1pla5h on 2009-01-07
No that didn't work. The restore and minimize buttons won't even respond.

---

### Post by adult swim on 2009-01-07
hmm try turning off compiz for a bit and see if that helps
press alt+f2 and enter in ```
metacity --replace
```

---

### Post by wh1pla5h on 2009-01-07
Yeah that fixed the sticking issue, but what should I do about Compiz? I like being able to have it running, but I don't understand why its not working. It worked the first time after I installed it.

---

### Post by slibuntu on 2009-01-07
I had a similar problem to the 2nd poster, and his workaround usually works.

Could you post a screenshot so we can see whats going on?

---

### Post by wh1pla5h on 2009-01-07
Oh, man this is bad. Now I can't even type anything. I'm typing this from my laptop and my desktop has all the windows stuck to the top panel so I can't do anything. Terminal won't even respond.


Scratch that. I was able to restart the pc and now it seems to be working. I guess I just can't use Compiz.

---

### Post by slibuntu on 2009-01-07
This doesn't sound like the bug that often happens with firefox and compiz. But I thought that that had been fixed by the latest updates. Have you got all of them installed?

---

### Post by wh1pla5h on 2009-01-07
Yeah I just recently installed all the updates. I still have a lot to learn about Ubuntu. I am very new at this.

---

### Post by Therion on 2009-01-07
If you're having trouble with Compiz messing with your Firefox windows (missing Minimize, Maximize and Close buttons) try this.

Open your Compiz Config Settings Manager (CCSM).  Find the "Utility" section and open the "Workarounds" plugin.  

**UN**-check the option at the top for **Legacy Fullscreen Support**.

If THAT doesn't solve the problem, open a Terminal and enter the following:```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```

You MAY need to log-out and log back in to effect these changes, I don't really remember if you do or not.

---

### Post by wh1pla5h on 2009-01-07
Thanks. Btw, you just reached 1337 posts. Thought that was quite funny.

---

### Post by Therion on 2009-01-07
Ahhhh Post Count.  It's a fleeting joy.

Did you get your FF issue resolved, by the way?  The Compiz plugin workaround fixed that same exact problem for me some time ago, but some people need to stop Emerald, hence the CLI stuff. 

I'm always curious to know what works.

---

### Post by wh1pla5h on 2009-01-07
Sorry for the late response. I had to step out. It seems like Compiz is causing the window sticking because when I re-installed it and then clicked "Reload Window Manager" it caused the windows to jump up and stick over the panel. And what's worse is that Compiz still doesn't work. I can't get any of the effects to work.

---

### Post by Therion on 2009-01-07
So did you uncheck the Legacy Fullscreen Support option in Compiz?

---

### Post by razar45 on 2009-01-07
Firefox is not working? >.<

---

### Post by Stine on 2009-03-15
Thanks, Adult Swim! Pressing f11 twice completely solved the problem I had with my Firefox window frame. Not a solution I would have been likely to come up with by myself, but an easy one nonetheless :)

---

### Post by Mr_B on 2009-04-18
> **adult swim said:**
> when Firefox messes up like that try hitting f11 two times
some people have reported a permanent fix that is that after they hit f11 two times, then they click the restore window button (the one between minimize and maximize) and then restart Firefox.

Thanks adult swim! Hitting F11 twice etc. fixed the problem for me. I had played with it and lived with it for several days - annoying. Thanks for the quick and simple fix!

---

