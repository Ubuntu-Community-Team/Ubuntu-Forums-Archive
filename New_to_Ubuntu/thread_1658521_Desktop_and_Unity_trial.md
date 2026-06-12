---
title: "Desktop and Unity trial"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by wiggy25 on 2011-01-02
Ok I know this has been posted before, well bits of it, but I couldn't find it! 
Thought I'd put it all in one place just for information on what I've found!
[LEFT] I have for the last few weeks been playing about with Ubuntu 10.10 Desktop version. 
 I really like it, you must remember I have been bought up on M$ so this Linux is completely new to me.  
Anyway, I've read that in the next release the Gnome GUI will be replaced with Unity, so I wanted to see what that was like.
Now in the Netbook version this actually uses UNITY, although running under Mutter, not compiz, when running under compiz it should be much faster!
In the Synpatic package manager if you type in UNITY and mark it for install it will install all the dependencies as well.
If you log out, the log in screen will appear for you to enter your password.
At the very bottom of the screen in the bottom panel it says Ubuntu Desktop version, with a drop down arrow next to it.
If you press this you then have the choice to log in using the Ubuntu Netbook version. 
Select this enter your password and it ***SHOULD*** open with the UNITY GUI, if it doesn't like mine!! it says that it can't run and tells you to select the Desktop version.
 Now I couldn't understand why this was, as I had installed compiz and had the 3D cube spinning round with all the different effects so seemed a bit odd.
Found that I needed to install a package from the terminal, which I found here on the forums.

```
glxinfo | grep render
```The output of this tells you if rendering is enabled or not, if not, which was the same as mine, I entered this:-

```
*sudo apt-get install mesa-utils*
```Which installed something, don't know what, but on entering the first command again, direct rendering was then enabled.

So I then rebooted and went into Ubuntu desktop, logged out (not full reboot) and selected netbook version logged in again.
This time Netbook version came up with no fault saying it couldn't run.

Still too new to all of this to understand exactly what I'm doing but thought I'd post this in case anybody else is having a problem and would like to try both without having to download both versions.

Nice to be able to try the Unity GUI, I know it will be different in Natty but nice to actually try it first.

Cheers

Ian
[/LEFT]

---

### Post by Spencer Caplan on 2011-01-03
I know that in Ubuntu 11.04 (which ships with Unity) if your computer does not have 3D acceleration enabled then upon login you will boot to the regular Gnome 2.32 interface. I don't know if the same works for running the Unity interface under 10.10, but do you have 3D acceleration enabled when you run regular Ubuntu Desktop Edition?

---

### Post by wiggy25 on 2011-01-03
I don't think the 3D acceleration is enabled when you install the Desktop version of Ubuntu

When you install Desktop edition, Compiz and Compiz config manager are not installed by default, I installed these later to be able to get all of the effects working.
This led me to believe that the graphics card( Intel G31 built in to motherboard ) would be OK for running Unity in the Netbook version.

I guess when you install Netbook edition from scratch it will automatically install the required drivers, packages and make sure anything else is switched on.

Just pleased to know that if Netbook Unity works on here then Ubuntu Desktop using Unity in 11.04 should also work.

Cheers

Ian

---

