---
title: "pidgin freezing"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by theacclaimed on 2009-02-01
I just installed ubuntu, and now whenever I try to use pidgin, it freezes only a few seconds after I'm signed in.  I noobishly tried reinstalling it through the synaptic package manager, but the problem persists.  Also it appears completely up-to-date.  The only thing I cant think of is that I was using pidgin right after my first boot, while it was updating, so maybe that screwed something up.  But reinstalling didn't do anything.

edit: it only freezes after I talk to someone or vice versa.

---

### Post by Crafty Kisses on 2009-02-03
Try running Pidgin in Terminal and see if you get any errors.

---

### Post by theacclaimed on 2009-02-04
Assuming that I did that correctly, (I just opened terminal and typed pidgin) the program opens like normal, I try to talk to someone, and the program freezes.  Nothing appears in the terminal, although to clarify on what happens. the pidgin windows turn gray and aren't interactive(obviously).  Like usual, I click to close it and say force quit, and in terminal it says killed.  No other errors.

---

### Post by skliarie on 2009-02-16
pidgin locks up for me after couple of minutes from startup as well.
I ran it under strace and recorded log file (see attached).

I have ubuntu 8.10, fully up-to-date. Up until yesterday everything worked, and pidgin was not updated lately.

ii  pidgin                                     1:2.5.2-0ubuntu1                   graphical multi-protocol instant messaging c
ii  pidgin-data                                1:2.5.2-0ubuntu1                   multi-protocol instant messaging client - da

---

### Post by freak42 on 2009-02-16
Your user settings related to pidgin are in a folder in your home director called '.purple' try moving/renaming this folder and pidgin should startup with all settings reset (of course your accounts will not be setup as well)..

if pidgin works better that way something in your settings was borked.

hth

---

### Post by era86 on 2009-02-16
Just for a little more detail, what chat service does it usually crash on (AIM, IRC, etc.)  I've noticed that mine crashes alot when I use Facebook chat.  Something to ponder...

---

### Post by skliarie on 2009-02-16
Looks like I have problem described [here]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/162701"). At least killing pulseaudio solved the problem for me.

---

### Post by colonelqubit on 2009-04-22
> **theacclaimed said:**
> I just opened terminal and typed pidgin...Nothing appears in the terminal

When trying to diagnose something by running it in the terminal, you can usually run it with a -d, --debug, or some similar switch which will output a lot more information about what's going on.

For example with pidgin you can type:
```
pidgin -d
```

---

### Post by Crowder on 2009-07-12
here's something interesting. When I ran Pidgin in debugging mode through the terminal, the problem completely disappeared. :-k

---

### Post by ee19921 on 2009-07-12
I have the same problem with pidgin. Currently running pidgin in debug mode. No problem so far. :confused:

---

### Post by Crowder on 2009-07-14
hey guys -  looks like i just got lucky for a while there. While running in debug, I had the freeze-up occur. I didn't see anything abnormal in the terminal, but I'm thinking it may have something to do with the musictracker plugin. Do any of you use it? Just curious. 

I doubt thats really the cause, since i usually get it when opening an IM, but I'm checking anyway. I've switched off musictracker for now - we'll see if i get any more errors (last one happened while musictracker was updating my status, trying to rule it out).

---

