---
title: "no back button in firefox"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-14
Just installed Jaunty from live CD.  All was well until I get a message box in Google Earth, something about openGL and needing to update graphics driver.

So I looked around in the forums and one suggestion was to open a terminal and run

compiz --replace

I did that, to my sorrow, and some weird things happened, the most annoying of which is the way firefox now runs.  I don't have any history nor do I have the use of the "back" and "forward" buttons.  The "refresh" and "stop" buttons no longer function, either.  These 4 are on the navigation toolbar at the left end.

I have no idea of what to do to correct this.  Any and all suggestions would be greatly appreciated.

---

### Post by wpshooter on 2009-06-14
My recommendation (perhaps not the one you want) would be to re-install Jaunty from scratch using either the safe graphics mode parameter or from the ALTERNATE (text based) CD version of Ubuntu.  And then try to find the "correct" (if there is one) Linux driver for your particular video card (but fair warning, this can sometimes cause more problems than it will solve, so if you can get a stock installation of Ubuntu installed and the video works correct, you might consider leaving well enough alone, at least for a while.

---

### Post by ddrichardson on 2009-06-14
Are you still running compiz? When you say the buttons don't work, are they missing, can you not click them or are they not doing anything when you do?

---

### Post by raymondvillain on 2009-06-14
Am I still running compiz?

I don't know.  I never told it to stop.

The buttons appear but are "greyed out".  I can click on them but they don't do anything.  And when I click on "History" a window opens but has no links in it at all.  Alt+left arrow (which is supposed to do the same thing as the back button) does not work.  Ditto Alt+right arrow.

Does this help?

---

### Post by ddrichardson on 2009-06-14
Have you rebooted?

---

### Post by raymondvillain on 2009-06-14
Yes I have.  At least I think so.  Should I do that again right now to make sure?

I have indeed rebooted.

When I did compiz --replace everything froze so I had to reboot.

Is this fatal?

---

### Post by ddrichardson on 2009-06-14
Do metacity --replace

---

### Post by raymondvillain on 2009-06-14
Just tried that.  Same thing:  Some windows flashed, then everything froze.  Had to reboot.

Firefox is still without the use of the back, forward, refresh, and stop buttons.  They are greyed out and unresponsive.

I'm about to chuck it all and re-install Jaunty from the live CD.

Any other ideas?  Thanks for your suggestions.

---

### Post by ddrichardson on 2009-06-14
Try reconfiguring Xorg first, you'll need to kill gdm:```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ajgreeny on 2009-06-14
Sorry, ddrichardson but the command ```
sudo dpkg-reconfigure xserver-xorg
``` no longer does anything and is a waste of time (since 8.04 I think).

It is not a surprise that the screen flickers when you run ```
metacity --replace
``` in the terminal, it always does because you are changing the window manager, but I am surprised also if it did not put you back to where you were at the start.

One other thing to try is to go to System-Preferences-Appearance and set the Visual Effects to "None" or you could temporarily uninstall compiz and reboot, then reinstall to try again if you want, but normally ```
metacity --replace
``` would do it and get rid of problems

---

### Post by raymondvillain on 2009-06-14
I did set appearance effects to none, alas, to no avail.

---

### Post by mc4man on 2009-06-14
you may also at some point want to identify what your display adapter is

```
sudo lshw -C display
```

note that it is now possible to install and test restricted drivers from a live cd environment (if they work on the live cd then they should on the 'real' install

---

### Post by raymondvillain on 2009-06-14
If I open a terminal window and type metacity --replace, how do I exit from metacity?  My terminal window seizes up and I have to ctrl-c to get out of it.  Even then the window sticks around but does not close and I haven't found a way to anything except reboot.

It looks like my 5 year old desktop (Pentium 4) is becoming more useless by the hour.  Maybe I ought to just drop back to Hardy since this equipment is so ancient.

---

### Post by ddrichardson on 2009-06-14
> **ajgreeny said:**
> Sorry, ddrichardson but the command ```
sudo dpkg-reconfigure xserver-xorg
``` no longer does anything and is a waste of time (since 8.04 I think).
I've not been keeping up with Xorg to be honest.

---

### Post by hyperdude111 on 2009-06-14
Try this

Go to Home the press "ctrl-H" go to the .mozilla folder.

rename the firefox folder to firefox.bak and it should work.

---

### Post by raymondvillain on 2009-06-14
All hail to thee, hyperdude111!

That did it.  Many thanks for your help.

Now if I could just get my bookmarks back.

---

### Post by ajgreeny on 2009-06-14
Your bookmarks are in the old ~/.mozilla.bak/firefox/*alphanum*.default folder and now in a file called **places.sqlite**.  Just copy that file back to the new profile folder and you're back where you were, bookmarks, anyway.

---

