---
title: "cursor cannot be seen after rousing from suspend or hibernate"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by hongqipilang on 2010-05-13
hi,, friends,, who can help me with my problem,I am using Lubuntu 10.04 LTS,when I put my laptop into suspending or hibernate, once I rouse it,, a boring problem appears,,I cannot see my cursor at all,,if I press the right key of the mouse,,it can open menu and I can move,, but I cannot see the cursor all the time,,what I can do is shutdown or reboot..

so who can give me an advice to fix this problem??

thanks a lot!

---

### Post by blazemore on 2010-05-13
Try running these commands:
```
sudo mv ~/.config/**monitors.xml **~/.config/[B]monitors.xml.old
[/B]
```

Should work now (possibly after reboot)

If you get an error from that, or that doesn't work, post here again. I'm subscribed to this thread.

---

### Post by ComputingFroggy on 2010-05-19
Hi,

I have a similar but slightly different problem.
I am running Lubuntu of a Fujitsu P2110 laptop and each time I come back from suspend mode the cursor is frozen and I can not move it.

I don't even know how to reset the Window Manager (on Ubuntu it used to be CTRL+Alt+Backspace) !

I am new to Lubuntu.
Thanks for your help,
L@u

---

