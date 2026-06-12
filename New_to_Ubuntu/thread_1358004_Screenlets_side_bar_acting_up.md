---
title: "Screenlets side bar acting up"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-12-17
Hi All,
 Okay, I am going to go nuts. I am on the verge of putting together a well put together desktop for myself to use. 

I am wanting to put the screenlets side bar on. I want to have the space reserved, so when I maximize my windows, it is maximized to the edge of the sidebar. I want the couple of screenlets I use to stick to the sidebar. Sounds simple right?

So, I can get the clock to stick to the sidebar when I have it reserved. But if I try to put anything else on it, it kicks the sidebar out to the left and leaves the screenlets to the right. If I do get the screenlets to stick, I can not adjust them, as the sidebar sits on top of them. ANd then it wont reserve the space for my windows. I am using Version 3? It is the one that came bundled in the screenlets from synaptic.

Anyone else have any issues with this? Oh, I am using Mint 8, based on Ubuntu9.10

Thanks

---

### Post by AndyP79 on 2009-12-18
*bump*

---

### Post by VOLKOV9 on 2010-01-25
Sorry, can't help.   Having a similar issue.  When I say "align right" or "left," it's fine, but when I say "alight right reserved" (or "left...") it leaves [width] pixels unoccupied, and aligns next to that.  I might not be describing it well, but a screenshot is attached.  It does however, reserve the correct screenspace,when I maximize some other window (see screenshot-1) - the problem is just that the sidebar itself doesn't occupy that space.  Pretty goofy.

Anyone have any advice?  I have a feeling whatever solves one of our problems will at the very least offer insight into the solution of the other.

---

### Post by VOLKOV9 on 2010-01-26
After rebooting, the behavior has changed: sidebar now aligns properly, but refuses to allow docking of other screenlets, regardless of whether the option to do so is checked.  It does allow me to move another screenlet directly on top of it, but every five or ten minutes it kicks it out.  Still odd.

---

### Post by noSelf on 2010-01-29
ditto here, on both my machines. bummer. maybe it's time to really learn Python....

---

### Post by VOLKOV9 on 2010-01-30
[https://bugs.launchpad.net/screenlets/+bug/291969](https://bugs.launchpad.net/screenlets/+bug/291969) is my problem.  Apparently it's a known bug with too low a priority for anyone's attention.

---

### Post by VOLKOV9 on 2010-01-30
Just wanted to say - this problem looks approachable, just noone's worked on it.  It seems to come down to this "_NET_WM_STRUT" thing with GTK - when some things get redrawn, they're put outside the reserved strut.  But somehow the people who wrote Gnome Panel for instance found a way to reserve screen space for something that changes.  So any ambitious coders out there wanna take a crack at it?

PS: Sorry for the double-post, but the edit button isn't working for me.

---

