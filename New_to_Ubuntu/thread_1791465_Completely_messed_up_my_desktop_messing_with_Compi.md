---
title: "Completely messed up my desktop messing with Compiz"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by BTXNick on 2011-06-26
I enabled a bunch of crap with Compiz like a jackarse and now I can't move windows. Firefox isn't even giving me the option of exited out/minimizing/changing the size. The entire bar that goes on the top of the screen is gone. I also installed Cairo, which gives it that applie-like bar on the bottom, and the one on the left is now gone. 

What do? Lol

---

### Post by jtarin on 2011-06-26
What version of Ubuntu are you using? Can you access a terminal?
On a number of distros, the actual Compiz binary is called compiz-bin. You'll probably want to be more forceful and try `killall -9 compiz`.

You'll also want to force another window manager to run:
DISPLAY=:0 metacity &
... if you're GNOME.

---

### Post by Eqi on 2011-06-26
The same thing happened to me. I never did find out what messed my computer up, but I just  did a bunch of reinstalls, purges, and restarts before everything seems to be working again. :-s

But I also just update to 11.04 so there would be issues with Compiz.

---

### Post by Blasphemist on 2011-06-26
For Natty at least, using this is a lot easier than reinstalling.
> If nothing helps reset Compiz configuration via tty and reboot. (Close all GUIs and save your work)
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot
```

[http://manpages.ubuntu.com/manpages/natty/en/man1/gconftool-2.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/gconftool-2.1.html)

Before playing with CCSM again, export the default .profile in order to reset after an occasional misconfiguration or press button 'reset' under 'preferences'.
Test plugins successive, if it works export profile files and give it a meaningful name.
Some plugins conflict with each other, such as wall vs. cube, static switcher vs. ringswitcher.
Workaround by disabling 'automated plugin sorting', after done enabling it again.
Examples.
[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/156305](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/156305)
[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty)


---

### Post by beew on 2011-06-27
> **BTXNick said:**
> I enabled a bunch of crap with Compiz like a jackarse and now I can't move windows. Firefox isn't even giving me the option of exited out/minimizing/changing the size. The entire bar that goes on the top of the screen is gone. I also installed Cairo, which gives it that applie-like bar on the bottom, and the one on the left is now gone. 

What do? Lol

You have disabled Unity, since you have the Cairo dock it is easy to fix, use the launcher in the Cairo dock to open CCSM  to re-enable Unity and other options that have been disabled.

You need under General:

Composite

Gnome Compatibility

OpenGL

then under Desktop:

check Ubuntu Unity Plugin

Under Window Management:

check 

Move Window

Resize Window

Scale

Static Application Switcher

Then logout and log back in. This should give you back the ability to move windows and resize them. You can add other features now but be careful about possible conflicts.

---

### Post by kidknapp on 2011-06-27
> **beew said:**
> You have disabled Unity, since you have the Cairo dock it is easy to fix, use the launcher in the Cairo dock to open CCSM  to re-enable Unity and other options that have been disabled.

You need under General:

Composite

Gnome Compatibility

OpenGL

then under Desktop:

check Ubuntu Unity Plugin

Under Window Management:

check 

Move Window

Resize Window

Scale

Static Application Switcher

Then logout and log back in. This should give you back the ability to move windows and resize them. You can add other features now but be careful about possible conflicts.

You may not even have to go that far....In the Compiz settings manager
under Window Management> Make sure Move Window and Resize Window are ticked. I had this problem in Natty and it was as simple as that.....

Let us know if any of the above helped/didn't help....:P

---

### Post by beew on 2011-06-27
> **kidknapp said:**
> You may not even have to go that far....In the Compiz settings manager
under Window Management> Make sure Move Window and Resize Window are ticked. I had this problem in Natty and it was as simple as that.....

Let us know if any of the above helped/didn't help....:P

But OP has bigger problem, Unity is disabled and Compiz was probably reset.

---

