---
title: "it freezes alot"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by freefixkorma on 2010-06-24
hello guys i am running on ubuntu 10.4 and notice lately that the system is freezing a little just a little sometimes when i scrolling the pointer from one place to another it takes couple of seconds to react ,and sometimes the screen is like loosing light gets like gray and comes up like if the power is very low in bulb and then comes up normal ,i was wondering what is i have a P4 dell 2.8 hgz 1.5 ram it was just fine dont know if was the installation on the new software is there a way to perform any diagnostic to figure what is the problem with it or ubuntu 10.4 is too heavy for my old Desktop thanks in advance for any guidance 

freefix

---

### Post by sikander3786 on 2010-06-25
Hi.

Can't figure out any thing else than thinking that your mouse might have got wierd. And for the screen going gray, try disabling the screen saver and extend time in Power Options for display.

Your pc is quite great capable of running Ubuntu so that might not be an issue.

Check your mouse and post back. I also had problem with mouse in the near past when I started thinking of a problem with OS but then realized that it was my mouse causing problems.

Regards.

---

### Post by Catharsis on 2010-06-25
That happens when the system gets bogged down, usually from a memory leak or something. Open up a terminal and type 'top' and watch for a process that's eating up either CPU or memory more than it should be.

---

### Post by k3lt01 on 2010-06-25
Catharsis has hit the nail on the head. Further to his suggestion I would suggest you might also try doing a memtest to see if that shows any problems. How much SWAP do you have? if your RAM is slowly giving up the ghost you will find your SWAP has to pick up the slack and if you haven't got much SWAP your system will bog down.

---

### Post by mikewhatever on 2010-06-25
What's the graphics card model?

---

