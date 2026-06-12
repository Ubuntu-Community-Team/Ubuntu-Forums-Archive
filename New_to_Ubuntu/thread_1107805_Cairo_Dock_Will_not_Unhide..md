---
title: "Cairo Dock Will not Unhide."
date: 2009-03-27
forum: New to Ubuntu
---

### Post by keinefurcht on 2009-03-27
I have googled variants of the thread title, and have come up with nothing useful.

I installed Cairo Dock and configured it. I know it is running over there on the right side of the screen, autohidden, because when I minimise a window it goes in that direction. However, when I mouse over where it should be...nothing happens. I cannot get it to un-autohide. I've tried removing it in Synaptic Package Manager and reinstalling, and it's still over there, mocking me. What to do?

---

### Post by fabounet on 2009-03-27
Compiz lets an extra pixel on the screen border, that you can't reach with the mouse. that makes triggerring the dock impossible if you set a size of 1 pixel height for the hidden dock.
and setting a bigger size will work, but you're sure to go out the dock just after you enter when your mouse will reach the screen border, if you don't take care of it.
so auto-hide on the right/left side with Compiz is not a very good option.

---

### Post by newb85 on 2009-10-17
I have a secondary dock that I placed on the side of my screen and auto-hid.  Since I can't unhide it, I don't know how to move it to the bottom of my screen.  Is there a way I can do this?

---

### Post by fabounet on 2009-10-17
I think it's a bug I've corrected this week.
You can try the weekly version on our PPA ([)]("https://launchpad.net/cairo-dock").
current version is 2.1.1-rc

---

