---
title: "Killing bash is a bad idea I take it?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by chemburn on 2009-04-28
so, i am almost positive this is going to make me sound like an idiot, but please bare with me. I had a dvd in my laptop, popped it out and the icon stayed on my desktop, when I try to unmount it, it says can't find mount point, when i try to open my dvd drive, its not opening or responding. So I ran fuser /media/cdrom and the pid it pulled up (25238c) is bash in the system monitor. Now i know rebooting will most likely fix this, but I was wondering if killing bash, I assume would actually be a bad idea, would fix this, and was hoping someone could shed a little light on what happened simply for my own educational sake. The other thing i was wondering is the c on the end of the pid? Why is it there and why isn't it showing in the system monitor (I went there to check the process name), but it comes up on the output for fuser.

This is really convoluted I'm guessing, and i would be happy to look it up myself like I usually do, but my attempts to find any real reference on google and the forum hasn't been very successful. Mainly because I am not even too sure what to search for. Any help would be greatly appreciated. Thanks in a advance!


P.S. I know there is a command to pull a name for an application's PID, I can't however find what it is, what would I use for that instead of looking the pid up in the GUI system monitor?

---

### Post by Dougie187 on 2009-04-28
For your P.S. question, try in a terminal "man ps"

Also, Killing bash should only kill your shell, in this case your terminal. And then you would probably have to close your terminal and open a new one, but I am not sure. There is only one way to find out what this would do, but in general I wouldn't say it's a terrible thing to kill bash. It's not going to ruin your computer or anything.

---

### Post by chemburn on 2009-04-28
well, that was ironic...thank you for the info on ps;)

---

### Post by llamabr on 2009-04-28
ps will help you put an app with a pid.  it usually goes:

```
ps aux
```

But there are other variations.

Killing bash will just log you out.

---

### Post by chemburn on 2009-04-30
thank you guys for the information and the patience, I have been using linux on and off for several years now without ever really getting beyond the "insert this line to get this result" stage, learning the inner workings of the OS is a lot of fun, very useful, and goes a great deal more smoothly with the expert resources on this forum. Much appreciated.

---

