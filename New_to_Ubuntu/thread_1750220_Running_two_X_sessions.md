---
title: "Running two X sessions"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by spillage2 on 2011-05-05
Hi All.

I have finally managed to set up my two monitors and got each one to show my desktop with spreading out my back ground image over both screens.

I am using the cube effect in compiz and when in use it now look messy as it display both screens side by side...sad I know but I want better.

I am sure I can run a seperate version of x on each screen and have looked around but so far have struggled.

I assume...I need to make a new user and then have them both log into a seperate version of x.

Can anyone provide me with a simple step by step guide thats idiot proof to follow..


Cheers 

Spill.

---

### Post by bodhi.zazen on 2011-05-05
I think what you are wanting to do is called "multiseating".

Knowing that will help you find a guide, there are several the come up on a google search.

I would start here:

[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

### Post by spillage2 on 2011-05-05
ok thanks for that I'm basically looking to do:

monitor 0 = x session 1 (user 1)
monitor 1 = x session 2 (user 2)

Have been googling multiseat but so far all keep commenting on using multiple mouse and keyboard.  


I guess that running one x session on each monitor with one mouse/keyboard is not possible...:(

---

### Post by bodhi.zazen on 2011-05-05
> **spillage2 said:**
> ok thanks for that I'm basically looking to do:

monitor 0 = x session 1 (user 1)
monitor 1 = x session 2 (user 2)

Have been googling multiseat but so far all keep commenting on using multiple mouse and keyboard.  


I guess that running one x session on each monitor with one mouse/keyboard is not possible...:(

Yes you need one mouse, one monitor (or more), and one keyboard for each X session.

multiseating = more then one user at at time.

You could write a custom xorg to start a separate X session on each monitor.

This link will get you started.

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

You will have to modify that to specify which monitor for which session and script a start up.

With that technique you can have only one user at at time.

---

