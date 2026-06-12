---
title: "title bar gone-what?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Xant on 2011-01-21
I updated to 10.4 last night, and today, when I booted up a curious thing seems to have happened. I lost my title bars. On everything. Is this normal? or has the title bar been removed sometime since 8.04?

I am not totally new to the block, but I dont think I know more than a well educated end user. With that in mind, could help be in simplish terms?

---

### Post by zeroseven0183 on 2011-01-21
Can you do something like this?
1. right-click on desktop
2. select Change Desktop Background, then
3. under Visual Effects tab, select Normal or None

See if that restores your window title bar.

Or you can also do ```
metacity --replace
``` in the Terminal assuming you're not running Compiz.

---

### Post by Xant on 2011-01-21
Thanks for the help, is it usual that normal doesnt have the window title bar?

---

### Post by zeroseven0183 on 2011-01-21
No. But it does happen a few times especially when (you or) your system is trying to change something about your display configuration.

---

### Post by willyclaes on 2011-01-22
I have a similar problem. I removed compiz because I couldn't enable desktop effects. I could enable it, but nothing happened. Sometimes the windows title bar disappeared. Everything worked before I updated to 10.04. After I removed compiz the windows title bar disappeared completely. So after a boot I enable metacity. I'm quite happy with metacity and I want to enable it by default (so after I boot I don't have to start it in a terminal every time). 

Also after a boot I can't use alt+f2 for some reason. I'm thinking all these things are related one way or another because after I enabled metacity alt+f2 works just fine. All of these problems started after I installed and then removed the Cairo dock.

tl;dr total noob wants to enable metacity by default because he couldn't handle compiz

---

