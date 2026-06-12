---
title: "console: starting software in background and then closing console"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by freak42 on 2009-03-01
Hello all,

I find this behaviour strange:

if i start an application in the console and then exit the console:
```
gedit &
exit
```

the application keeps running, however if I start the application in the console
```
gedit &
```
and then exit the console by right-clicking on its gnome-window menu bar entry and choose close from the menu the foreground application will also close?

why is that?

thanks in advance for any enlightenment

---

### Post by Xiong Chiamiov on 2009-03-01
I don't have experience with gnome terminal in particular, but I know that in my terminal emulator, typing 'exit' will close the particular instance I have open.  So, if I have multiple tabs open, it closes the one I'm in, and switches me to the next one.  When exiting the last one, the app sees that there are no more to switch to, so it just kinda closes.  When closing the whole application, however, it probably goes through and terminates every process it started, or somesuch.

This is all just speculation.

---

### Post by Largaroth on 2011-06-13
Ah digging up an old thread I can see ^^.

I wanted to know, is there anyway of setting the terminal up so that if I close it through my gnome interface (clicking on the close button) that it acts like an
```
exit
```
 ?

Because I constantly lose data like this ^^". (I know, I'm terrible because I don't save regularly). Because I write a lot of stuff, and so I like to leave the window open and just work on it a little bit at a time.

Any help would be much appreciated.

---

