---
title: "no normal graphic interface upon booting"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by vjrb2 on 2010-05-23
Hello all,

I'm an absolute beginner and I've recently upgraded to 10.04 Lucid on a Dell laptop. Upon booting I get only a terminal window instead of the usual ubuntu graphic interface. Anybody could help?

Thanks!
Vincent

---

### Post by TeoBigusGeekus on 2010-05-23
What happens when you type
```
startx
```

---

### Post by vjrb2 on 2010-05-23
Hi, 

I get several lines of error message, do you know how I could copy them to show you? I'm currently switching from firefox to terminal but I don't know how to copy text from there to paste in firefox.

Thanks!

---

### Post by vjrb2 on 2010-05-23
OK I'll try to type it manually:
it says:

hostname: Name or service not known
xauth: /home/vincent/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/vincent/.Xauhority
xauth: error in locking authority file /home/vincent/.Xauhority
xauth: error in locking authority file /home/vincent/.Xauhority

Fatal server error:
Sever is already active for display 0
       If this server is no longer running, remove /tmp/.X0-lock and start again

Please consult the X.Org Foudation support at http//:wiki.x.org for help

ddxSigGiveUp: Closing log
xauth: error in locking authority file /home/vincent/.Xauthority

---

### Post by TeoBigusGeekus on 2010-05-23
Try this then
```
sudo rm /tmp/.X0-lock
```
and then again
```
startx
```

---

### Post by TeoBigusGeekus on 2010-05-23
As a side note however, I should tell you that you should never upgrade your system - a clean install will always be the best solution.
If you have a separate /home folder everything would be perfectly smooth.

---

### Post by vjrb2 on 2010-05-23
Typing the lines you suggested above gave many lines of errors, do you know how I could copy them (I'm switching from a terminal to firefox by using Ctrl+Alt+F6), so that I could show it to you? It's too much to be memorised and typed by hand.

Thanks so much!

---

### Post by vjrb2 on 2010-05-23
When I type your first line I get:

rm: cannot remove '/tmp/X0-lock' No such file or directory

Then if I still try to do startx I get a similar message to before

---

### Post by vjrb2 on 2010-05-23
How do I do a clean install? The upgrade is being suggested by the update manager application. If I do a clean install will all the contents of my computer be saved?

---

### Post by Mark Phelps on 2010-05-23
> **vjrb2 said:**
> When I type your first line I get:

rm: cannot remove '/tmp/X0-lock' No such file or directory

Then if I still try to do startx I get a similar message to before

That's because you typed it wrong ...  Look at the command closely this time.  There is a period after the /tmp/ -- that indicates this is a hidden file.

---

### Post by vjrb2 on 2010-05-23
Hi
It gives me the same when I include the period

---

### Post by vjrb2 on 2010-05-23
Hey guys,

Any more ideas on that?
Thanks!
Vincent

---

