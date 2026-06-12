---
title: "Deep Trouble : Firefox not launching!"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-25
ok so this is the deal : i installed both alphatabs and tabsontop addons, then restarted firefox. but it failed to start and this is the js error i get:
```
Error launching browser window:no XBL binding for browser
```

---

### Post by DavidOfLondon on 2010-08-26
The reason you're not getting responses is your post is very vague without mentioning your OS.

Are you on Ubuntu? I've added dozens of addons in Firefox with Ubuntu 10.04 and not had a prob. The most likely scenario is you've added something that has created a conflict with another prog.

Your best option is to remove Firefox completely and reinstall but without knowing what OS you're on I can't advise.

David.

---

### Post by fremantle on 2010-08-26
umm what os i use is right there under my name xD

---

### Post by fremantle on 2010-08-26
can i browse to the firefox folder and remove the add on manually?

---

### Post by wojox on 2010-08-26
Did you try running 

```
ps -ef | grep firefox
```

See if there's any other firefox process running and killing them, then launching it?

---

### Post by fremantle on 2010-08-26
I killed all firefox processes but still get that message. i think that the two addons i installed conflicted with each other and so firefox cannot start becoz of a javascript error. heres the descriptions of the two addons:

Alphatabs
[HTML]Try to get better tabs... This replaces the menu bar with a special tabs bar, and allows the user to iconify tabs (and remember them for the next time)[/HTML]

Tabs On top: Puts the tabs all the way up above the menubar

---

### Post by fremantle on 2010-08-26
NEVERMIND, I JUST GOT THE SOLUTION
```
firefox --safe-mode
```

---

### Post by wojox on 2010-08-26
> **fremantle said:**
> can i browse to the firefox folder and remove the add on manually?

I'd try that route. Maybe just rename the extensions folder.

---

