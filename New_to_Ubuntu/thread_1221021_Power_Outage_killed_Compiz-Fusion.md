---
title: "Power Outage killed Compiz-Fusion"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by rednano12 on 2009-07-23
**THIS PROBLEM HAS BEEN SOLVED. THANK YOU DURDEN FOR THE HELP**

Hello all. 

Yesterday, in my area, there was a large thunderstorm, and the power got cut for a few minutes. My Desktop was forced to turn off, and it immediately turned back on when the power came back. However, the GDM did not load. I got stuck with the default spinny cursor. I thought it might take a while, but after a couple hours, I got fed up with waiting and went into tty1 to kill X. I reinstalled the NVidea drivers, but no cigar. I then went into recovery mode and ran xfix and dpkg. That seemed to do the trick.

When I logged back into Ubuntu, I opened up Firefox with Gnome-Do (which I have set to run on startup), but the top bar (with the minimize, maximize, and close buttons) was gone. Thankfully, I have an app called fusion-icon, which lets me edit these settings with a right click on the panel. I tried reloading the window manager, and I got nothing. My Compiz settings are not sticking, as when I change the number of horizontal desktops, the bottom panel still displays 2, even when I reload the window manager. Emerald is not displaying either. 

I am running 8.04.3 Hardy, with all of the latest updates. My graphics card is a NVidea GeForce 6200 that is capable of running Compiz. Please help! 

Thank you!

Rednano12

---

### Post by Durden on 2009-07-23
So do I understand correctly, you do not have a window-manager running at all? Does alt+f2 work?

---

### Post by rednano12 on 2009-07-23
Alt-F2 works. I am currently running Metacity however, and would prefer to be using Compiz. Emerald isn't working either and I am running GTK Window Decorator.

---

### Post by Durden on 2009-07-23
If you press alt+f2 and then type: emerald --replace
What happens?

---

### Post by rednano12 on 2009-07-23
Absolutely nothing. The style does not change from the original Human theme I had.

---

### Post by Durden on 2009-07-23
if you do it in a terminal do you get any error messages?

You can try to uninstall and then reinstall it:
sudo apt-get remove compiz

Then reinstall:
sudo apt-get install compiz

You can also reset gnome to defaults by:
rm -rf .gnome2*
rm -rf .config
rm -rf .gconf*

You may wan to back those up first just in case. Once you remove those log out and then back in.

---

### Post by rednano12 on 2009-07-23
If I do emerald --replace in terminal, the blinking cursor goes down a line, and I get no prompt. Again, nothing happens. I'm fairly certain that the warnings at the top of the page say to not rm -rf anything. what are these files that you are pointing to?

EDIT: I think I have figured out the problem. If I go to System -> Preferences -> Appearance and click on the Visual Effects tab, none is checked. If I try to change it, I get an error message that it could not be enabled. I'm going to reinstall the NVidea drivers.

EDIT2: Problem solved. Reinstalled drivers, and are good to go!

---

