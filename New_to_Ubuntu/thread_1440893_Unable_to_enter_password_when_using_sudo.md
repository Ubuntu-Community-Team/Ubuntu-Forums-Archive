---
title: "Unable to enter password when using sudo"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Bulwark on 2010-03-28
Ubuntu Linux ver 9.10.  Absolute Newbie.   Have been trying to fly with Ubuntu for a couple  of weeks, installed without problems, bought the book, downloaded the  command cheat sheets, experimented offline - no major hassles.  

I  now have a problem with the user password when trying to use the sudo  command (and it has been working).  I've done something which stops the  user password being entered, the password bullets do not appear  on-screen and a blank password is not accepted.  It's almost as if the keyboard has been locked but at least the Enter key works.  I appreciate that a  re-install will probably fix this but don't want to get into the habit  of re-installing to fix what could be simple to rectify.  Re-booting  does not fix the problem.  Any ideas appreciated.

---

### Post by Pollox on 2010-03-28
Note that when typing in your password for sudo, nothing appears on screen, but it is working.  That is, type in your password and hit enter, even though you won't see any password bullets.  This is normal behavior.

---

### Post by zsee on 2010-03-28
in the terminal when you enter sudo the password does not show up and this is perfectly normal. Just type in the password and press enter.
Or if this isn't your problem, try gksudo.

---

### Post by BikeHelmet on 2010-03-28
I'm guessing that those other posters nailed the issue.

But I would like to mention that on one PC of mine with a crummy VIA chipset, Ubuntu 9.10 had a glitch with my USB keyboard, and wouldn't accept any input for the password dialog. This made it rather difficult doing...well... anything. I wiped out 9.10 and installed 9.04, which works fine.

---

### Post by underquark on 2010-03-28
I've once seen a condition where sudo wouldn't work (i.e. typing in the password and then pressing enter just resulted in a new line being shown).  I had to re-start.  I think it is mentioned elsewhere.

---

### Post by lovinglinux on 2010-03-28
> **underquark said:**
> I've once seen a condition where sudo wouldn't work (i.e. typing in the password and then pressing enter just resulted in a new line being shown).  I had to re-start.  I think it is mentioned elsewhere.

That's normal behavior too. If you enter a command that doesn't produce any output and the command runs properly, then all you get is a new line.

---

### Post by Bulwark on 2010-03-29
With your help the problem is resolved.   Thank you all.

---

