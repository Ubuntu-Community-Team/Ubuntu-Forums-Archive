---
title: "loading programs not in launcher"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Wray on 2011-06-11
Complete noob here.

What is the best way to load installed programs that are not on the launcher?

I am trying to load Compiz screen manager.

I had Orca installed, all the configuration boxes at startup were greyed out, so 
that when i loaded it it went to VERY LARGE magnification with the mouse pointer locked to the crosshairs.  Pretty useless!

I downloaded Compiz - or, at least i thought i did _ but all that loaded was the config
screen.

Told ya i was a noob!

---

### Post by VOT Productions on 2011-06-11
Press ALT+F2 and type **compiz --replace**

---

### Post by Wray on 2011-06-11
> **VOT Productions said:**
> Press ALT+F2 and type **compiz --replace**

hangs my system, requirea a power off...[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by VOT Productions on 2011-06-11
Hmm... Do you have the CompizConfig Settings Manager?

---

### Post by Wray on 2011-06-11
> **VOT Productions said:**
> Hmm... Do you have the CompizConfig Settings Manager?


Yes...

---

### Post by VOT Productions on 2011-06-11
Is the "unity" profile selected?
Also... why are you trying to load Compiz?

---

### Post by Wray on 2011-06-11
> **VOT Productions said:**
> Is the "unity" profile selected?
Also... why are you trying to load Compiz?

I had config on the loader now it is gone!
I had config loaded and could see bunches of check boxes none of which
was Unity.
Very confused...i get stuff disappearingfrom the loader all the time.

I just need a simple screen magnifier.  While it looks like compiz has many more features than i need, it would be fine if i could get to run.

---

### Post by wildmanne39 on 2011-06-11
> **Wray said:**
> I had config on the loader now it is gone!
I had config loaded and could see bunches of check boxes none of which
was Unity.
Very confused...i get stuff disappearingfrom the loader all the time.

I just need a simple screen magnifier.  While it looks like compiz has many more features than i need, it would be fine if i could get to run.
Hi, what version of ubuntu or you using? if you are using natty it comes with compiz installed, it uses compiz and it must have it, you have to install ccsm to change settings of compiz and that is a bad idea to change settings you will break unity, which it sounds like you may have already done, if you are using unity follow the directions in my signature that says how to reset unity and compiz and just reset unity, then if you want to make changes to compiz come back here and I will give you a guide to help with that.

---

### Post by VOT Productions on 2011-06-11
Actually... its not a bad idea if you use it right. Try the magnifier or the Enhanced Zoom Desktop in ccsm.

So... try: unity --replace and compiz --replace. If that hangs, try it in Terminal (make sure NOT to close it!)

---

