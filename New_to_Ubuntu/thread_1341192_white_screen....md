---
title: "white screen..."
date: 2009-11-29
forum: New to Ubuntu
---

### Post by arashiko28 on 2009-11-29
I have 3 users on a computer and one of them doesn't composite screen and when I try to load compiz or emerald, I get a white screen and have to restart... how do I solve this?

---

### Post by NoaHall on 2009-11-29
Well, delete their settings by doing ```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
``` in a terminal.

Make sure you cd to their /home/user/ first.

---

### Post by Redmage913 on 2009-11-29
That code looks slightly dangerous, from what I've read on other posts regarding terminal terminology (forgive the pun).  As someone not used to the commands of linux terminals (I'm MS-DOS trained so there's a lot to unlearn), would someone mind explaining the code a bit?

---

### Post by arashiko28 on 2009-11-29
> **Redmage913 said:**
> That code looks slightly dangerous, from what I've read on other posts regarding terminal terminology (forgive the pun).  As someone not used to the commands of linux terminals (I'm MS-DOS trained so there's a lot to unlearn), would someone mind explaining the code a bit?

> rm -rf .gnome .gnome2 .gconf .gconfd .metacity

This is meant to completely delete gnome and it's configuration along with metacity, if you ever dare to do this just by copy paste, you will loose even your terminal and will be left with absolutely nothing but an empty session, it's not my interest, I have done it before, it's harder to put back than installing from 0.

rm stands for remove and only deletes the index of the directory while data is still there. Meaning, used alone, data is recoverable, not easy, but can be done. While -rf will delete everything included in a directory. Bottom line, if you are 100% sure you don't want to see it ever again, use it, other wise, stay away from these commands.

PD: always have installed konsole, it's KDE terminal, if your gnome ever fails, you have a way to work it back.

---

### Post by Redmage913 on 2009-11-29
So was the response completely invalid to your question?  If so, I have no problems reporting the response.

---

### Post by NoaHall on 2009-11-29
What are you talking about? It's not dangerous. It will simply delete the gnome config settings for that user. If you use it outside their /home/, nothing will happen, because those files exist only inside /home/user.

There is no single way that doing that command will cause damage to any software, it will simply delete that users settings.

Google it! It's the standard way to delete a users settings, when you are experiencing a certain user-only problems.

If you still don't believe me, see this thread - [http://ubuntuforums.org/showthread.php?t=419162](http://ubuntuforums.org/showthread.php?t=419162)

---

### Post by NoaHall on 2009-11-29
<snip>

---

### Post by Redmage913 on 2009-11-29
Hey, I'm just trying to learn.  I would have waited a reply before doing anything of the sort.  I did not fully understand the response.  Please do not worry, I have done nothing.

From the response:

> This is meant to completely delete gnome and it's configuration along with metacity, if you ever dare to do this just by copy paste, you will loose even your terminal and will be left with absolutely nothing but an empty session, it's not my interest, I have done it before, it's harder to put back than installing from 0.

rm stands for remove and only deletes the index of the directory while data is still there. Meaning, used alone, data is recoverable, not easy, but can be done. While -rf will delete everything included in a directory. Bottom line, if you are 100% sure you don't want to see it ever again, use it, other wise, stay away from these commands.

I thought the person meant that the code given was bad.  Completely agreed, I know little of this, which is why I was clarifying it as much as I could to learn more about how the Linux console works.

Again, my apologies.

---

### Post by NoaHall on 2009-11-29
> **Redmage913 said:**
> Hey, I'm just trying to learn.  I would have waited a reply before doing anything of the sort.  I did not fully understand the response.  Please do not worry, I have done nothing.

From the response:



I thought the person meant that the code given was bad.  Completely agreed, I know little of this, which is why I was clarifying it as much as I could to learn more about how the Linux console works.

Again, my apologies.


Okay, I'm sorry too. It's just a little annoying when people tell me something is something when I know it isn't :) No hard feelings.

---

### Post by Redmage913 on 2009-11-29
Agreed, no hard feelings.  Gotta love absolute miscommunication.

---

### Post by NoaHall on 2009-11-29
Hehe.

Anyway, to OP, have you tried it yet?

---

### Post by arashiko28 on 2009-11-29
> **NoaHall said:**
> What are you talking about? It's not dangerous. It will simply delete the gnome config settings for that user. If you use it outside their /home/, nothing will happen, because those files exist only inside /home/user.

There is no single way that doing that command will cause damage to any software, it will simply delete that users settings.

Google it! It's the standard way to delete a users settings, when you are experiencing a certain user-only problems.

If you still don't believe me, see this thread - [http://ubuntuforums.org/showthread.php?t=419162](http://ubuntuforums.org/showthread.php?t=419162)

I just explained what could happen if he used the code. Besides it's not only one user, if I leave one session running, the other will get the whiteout. And if you have only one session as in a truly personal computer, you will wipe out your user, that's why I wasn't intended to do it, I would have start from scratch with the 3 sessions.

---

