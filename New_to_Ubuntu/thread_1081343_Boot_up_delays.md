---
title: "Boot up delays"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by suitedaces on 2009-02-26
I recently upgraded to 8.10 from a wubi-installed 8.04. When I boot up, the orange block that moves along the screen (as opposed to the orange bar that will fill up) will just stop. Initially I left it as I assumed it was just loading. However, it hadn't moved after a full ten minutes. 

This now happens every time, but I have noticed that when I hold down "return" or a directional button, it will began to move across, then back again in the opposite direction, and back and forth, for around 10 seconds, then it fills the orange bar and loads up as normal.

While the delay is irritating, I am worried that it's hiding an underling problem.

I hope I have described this clearly enough for you to know what the problem is.

---

### Post by avtolle on 2009-02-26
What you describe is a problem with the kernel used in 8.10 (and, I must add, the same problem occurs in openSUSE 11.1 and Linux Mint 6) and certain computers (primarily, in my experience HP and Compaq laptops). What I have found is that when the "hang" occurs, a quick press on the power button (on my Compaq laptop) allows the boot to continue. Before I found that, I'd need to hold down a key (control, usually) to get it moving, and I'd need to press it more than once to complete the booting process. As near as I can tell, there is not any underlying "problem" as such other than the problem with getting the boot process going. My daughter's Dell laptop doesn't have this problem, so there is something with HP's implementation of something that causes the problem, IMHO.

---

### Post by suitedaces on 2009-02-26
Right, now I appear to have lost my loading screen completely. Whenever I try to let it go onto it (by not pressing esc for menu), it takes me to walls of text, and freezes intermittently, thought hitting return works. Eventually it gets to "reading files needed to boot". After some more loading text, it presents me with a recoevery menu: resume; clean; dkpg; fsck; root; and xfix. I don't know how waht to do, so I choose resume to be safe. Then i can log on and use the laptop as normal (it's this one I'm using to write this). 

Any ideas what's wrong?

---

### Post by suitedaces on 2009-02-26
This is now happening every time.

---

### Post by suitedaces on 2009-03-01
> **suitedaces said:**
> This is now happening every time.

Got this sorted out. Am I right to assume there are no fixes for the original problem?

---

### Post by suitedaces on 2009-03-01
Apologies for the bumping, I just know how fast these threads move.

---

### Post by avtolle on 2009-03-01
> **suitedaces said:**
> Got this sorted out. Am I right to assume there are no fixes for the original problem?
None that I know of. I just "hit" the power button once, and it continues without further intervention on my part. Clumsy, to be sure, but it works for me.

---

### Post by suitedaces on 2009-04-22
I didn't think this question was worthy of a new thread, but will this still be an issue in jaunty?

---

### Post by skymera on 2009-04-22
I had no issues when i was running Jaunty.

Jaunty is on a different kernel now anyway :) 2.6.28 afaik

---

