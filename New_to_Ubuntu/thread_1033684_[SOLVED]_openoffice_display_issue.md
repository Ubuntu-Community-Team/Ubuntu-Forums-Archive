---
title: "[SOLVED] openoffice display issue"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Drubie on 2009-01-07
Morning,

My OpenOffice writer is freakin out!  It automatically goes to a useless fullscreen mode and I cannot get out, when I scroll or mouse over a toolbar button, or even pull down a menu, the screen flashes black and does other wierd things.

I have tried looking under tools - options, but cannot find a fix.
I have also tried reinstalling through the synaptic.

None of the other openoffice apps do this, so is there something wrong with the writer, or with my display options?
I dont know what is going on...

---

### Post by whoop on 2009-01-07
have you tried removing .openoffice.org2 from your user directory (back it up)?

---

### Post by Drubie on 2009-01-07
is that an ibex thing?  im running hardy...

I cannot find the file .openoffice.org2 in the usr directory
searching now, lets see if its somewhere else

---

### Post by Drubie on 2009-01-07
> **Drubie said:**
> 
searching now, lets see if its somewhere else

nope, not found...

however, everything seems to be working as before...
spooky

Thanks for your help whoop

---

### Post by whoop on 2009-01-07
Applications have a .directory in the user dir (for user config settings). All files starting with a "." are hidden by default. To view these hidden files you should enable hidden files in your directory browser (in nautilus View-->Show Hidden files). Removing the . directory of a package should restore its default settings.

But don't touch it if it's working ;-)

---

### Post by addiebk on 2009-01-09
My mom's openoffice suite seemed to be having the same issues.  I reinstalled, which did not help, but then I entered full-screen mode (CTRL-SHIFT-J), and then re-entered 'normal' mode.  This seemed to fix the issue on this computer.

---

