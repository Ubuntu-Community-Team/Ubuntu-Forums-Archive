---
title: "Cut-And-Paste In 10.04.2"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by rs321 on 2011-07-04
Folks,

I'm trying to install Java in 10.04.2 and one of the instructions is to cut and paste a few lines to the terminal.  Not finding any special instructions on it, I used the Windows method of CTRL+C for cut and CTRL+V for paste but that doesn't work.  It doesn't do anything at all so how do I cut and paste in 10.04.2?

-Randy

---

### Post by nosehat on 2011-07-04
Ctl-C and Ctl-V works fine for most things, but for the terminal you need to use Ctl-Shift-C and Ctl-Shift-V for cut and paste.

Good luck.

---

### Post by rs321 on 2011-07-04
nosehat,

Thanks, but that didn't work in the Applications\Accessories\Terminal on my machine.  Is that the right terminal?  Is there more than one terminal?

-randy

---

### Post by nosehat on 2011-07-04
That's the terminal.  Maybe the clipboard was empty?

When you open your terminal window, click on "Edit" in the menu bar at the top of the window.  Copy and Paste should be listed as options there, with their keyboard shortcuts.  What do you see there as the keyboard shortcuts?

---

### Post by mcduck on 2011-07-04
> **rs321 said:**
> nosehat,

Thanks, but that didn't work in the Applications\Accessories\Terminal on my machine.  Is that the right terminal?  Is there more than one terminal?

-randy

It should work in pretty much every terminal, and it definitely does work on the Gnome-terminal (the one included by default in Ubuntu). Just remember that you can't close the application where you are copying from before you paste, it's a direct copy and there isn't any clipboard (unless you install one yourself).

Anyway, even better way of copypasting with terminals is simply highlighting what you want to copy, and then middle-clicking where you want to paste it. (the same works in other apps as well)

...also the right-click menu in Gnome-terminal also includes the options for copy & paste.

---

### Post by rs321 on 2011-07-04
mcduck,

The middle-click method worked great and now all I need to do is get it to allow me to enter my password.  I have never been able to enter my password in the terminal.

-Randy

---

### Post by nosehat on 2011-07-04
When you type your password in the terminal, the cursor doesn't move and there's no indication any typing is taking place.  That's normal.  Just type it in and press enter and it should work.

---

### Post by rs321 on 2011-07-04
nosehat,

Thanks to your generosity and patience what you suggested did the trick.

What bugs me is that "Ctl+Shft+C" is not a command operation that is intuitively obvious to the casual user and one I would not have guessed.  I would like somebody (me?) to make a list of commands and where and when to use them, or if there is already such a list will somebody please bring it to a newbie's attention?  It would sure save a lot of time and frustration while learning this beautiful OS.

Thanks again to all.

-Randy

---

### Post by nosehat on 2011-07-04
No problem.  The reason the terminal uses different shortcut keys for copy and paste is because you sometimes need to enter control characters into the terminal (^C to kill a process, for example).  So they added the shift keys for copy and paste to distinguish them from entering control characters.

You can find a good list of keyboard shortcut commands [here]("http://maketecheasier.com/useful-shortcut-keys-in-ubuntu/2008/07/14").

Have fun with Ubuntu!

---

