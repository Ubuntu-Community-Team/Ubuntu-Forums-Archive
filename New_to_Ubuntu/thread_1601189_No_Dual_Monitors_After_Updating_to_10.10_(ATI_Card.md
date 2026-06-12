---
title: "No Dual Monitors After Updating to 10.10 (ATI Card),"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by dyintrovert2 on 2010-10-19
I originally installed 10.04 from the Live CD and my dual monitors worked (nearly) flawlessly.  After updating to 10.10 this weekend my settings reverted to Mirror Screens and I've been unable to switch back.

Using Monitor Preferences, I uncheck the "Same image in all monitors" box and click Apply.  I receive "Please log out and log back in again".  Logging out and back in doesn't have any affect.  

I've also tried variations throughout Monitor Preferences.  Any changes that involve undoing the mirror does the same.

I have an NEC primary monitor and an Acer widescreen as my secondary.  I run an ATI RV730XT (Radeon HD 4670) on a 64 bit ubuntu 10.10 install.

---

### Post by MistaHardkill on 2010-10-20
> **dyintrovert2 said:**
> I originally installed 10.04 from the Live CD and my dual monitors worked (nearly) flawlessly.  After updating to 10.10 this weekend my settings reverted to Mirror Screens and I've been unable to switch back.

Using Monitor Preferences, I uncheck the "Same image in all monitors" box and click Apply.  I receive "Please log out and log back in again".  Logging out and back in doesn't have any affect.  

I've also tried variations throughout Monitor Preferences.  Any changes that involve undoing the mirror does the same.

I have an NEC primary monitor and an Acer widescreen as my secondary.  I run an ATI RV730XT (Radeon HD 4670) on a 64 bit ubuntu 10.10 install.

I am having the very same issue, but with a 5870 video card. Dual monitors seem to work fine until I install the video driver. I've tried the new beta driver as well to no avail.

I have a feeling nobody knows, nobody cares, or its a dead issue.

---

### Post by brookie on 2010-10-20
Hello,

The Maverick release notes stated that there was an issue with dual monitors towards the bottom of the page under "[Graphics Displays]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes")". It's good practice to always read the release notes before upgrading, then decide if you want to upgrade or not.

As for dual monitors on 10.04 I have found that the external monitor only works on the right side. I also have to drag the monitors one up on the left, and one down on the right, so that a large virtual screen is created by xorg (login, logout). 

If I don't do this the external always comes up as mirrored. Also, if I put the  external on the left, it never works either. Like applications opening on the wrong screen instead of the default main screen.

After the virtual line is added, I can move them back to where I had them (main on left, external on right).

Note that visual effects won't work with a large virtual screen. You can turn them off under System>Preferences>Appearance>Visual Effects = None. More info about a virtual screen size larger than [2048x2048]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"). 

Good luck, and hope the graphics display bugs are fixed soon. 

Cheers,
brook

---

### Post by dyintrovert2 on 2010-10-21
> **brookie said:**
> Hello,

The Maverick release notes stated that there was an issue with dual monitors towards the bottom of the page under "[Graphics Displays]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes")". It's good practice to always read the release notes before upgrading, then decide if you want to upgrade or not.

[Graphics Displays]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes") references [619663]("https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/619663"), which is listed as Fix Released.  If this were causing the issue, shouldn't the Update or Synaptic Package Manager have provided the correction?

---

### Post by dyintrovert2 on 2010-10-23
I've reinstalled 10.04 and my monitors work perfectly again.  Updates to 619663 hint at a regression release, so I may try 10.10 again in a few months.  Probably run a test from a separate partition or the Live CD first.

---

### Post by brookie on 2010-10-23
Glad you got it working again. I really like Lucid. I would like to try a newer kernel with Lucid at some point but I don't want to hose my system. For now have fun and good luck.

---

### Post by Rob_EE on 2010-12-02
I ran into this same problem while doing a new install of 10.10 today.  Instead of using the Ubuntu Monitor config panel, I got it working with the ATI Catalyst Control Panel.  It needed to do a reset before it took the changes, but I'm now running with non-mirrored dual monitors in 10.10 on the ATI drivers.

---

### Post by atgfx on 2010-12-06
After trying a few things you all said, I think I may have figured out a work around for this issue.  Here are the steps I took...

[LIST]
[*]Unchecked "Same image in all monitors"
[*]Clicked Green Monitor and drug it down slightly
[*]Clicked Apply
[*]It asked me a couple questions about virtual resolution...
[*]Then, it allowed dual monitors
[*]The only issue was the resolution being bigger than my monitor.
[*]Fixed this by taking green monitor and making it perfectly in-line with the red monitor.
[*]Didn't have to log out.
[/LIST]
New to the forum and Ubuntu...  Be gentle if this sounds ignorant, just trying to help out.  I hope it does.  Don't know if this is a permanent fix or not, works for now though.

@

---

### Post by possibarendless on 2010-12-17
I got this to work:

1) Administration->Additional Drivers->Enable/Install ATI driver
2) Install Catalyst Control Center (package fglrx-amdcccle)
3) Restart
4) Run Catalyst Control center as admin (sudo /usr/lib/fglrx/bin/amdcccle)
5) Display Options-> check Xinerama box
6) OK and restart

This is a huge downside to upgrading to 10.10. The fglrx driver failing on upgrade wasted an hour of my time easily (the random lines and squigglies and the required recovery of fglrx was disconcerting at the least).

---

### Post by joag on 2010-12-20
I ran into the same issue and after poking around with it and with some help I got it working, you can see how here:

[http://www.nixheiser.org/DualMonitor](http://www.nixheiser.org/DualMonitor)

I made the guide for FreeBSD and Slackware but right now I'm using Maverick and the same guide helped me here.

_______
joag

---

### Post by Devasto on 2010-12-31
I was able to get this information from ThinkWiki for linux.  Sorry I don't have the link, I printed out the instructions and logged in through tty1 (CTRL ALT F1).  You have to rewrite your X config file to recognise the new display settings.  

1.  Log in to tty1 (CTRL ALT F1)
2. Stop your X server: sudo /etc.init.d/gdm stop
3. Ensure your external monitor is plugged in
4. Type sudo X -configure
5.  It will give a message that the new xconf file is in use.
6. Type startx to get out of the CLI and back into the GUI
7. Try it out

This worked for me, and I have done a reboot just to test and haven't had any problems

---

### Post by corncob on 2011-01-11
I've plugged an external monitor into my Gateway NV54 running Maverick and its working fine except that there are boxes in the upper left corners.  One says "Laptop" and the other says "ViewSonic Corporation 19".  I know which monitor is which so I'm wondering if there is any way to remove them?  The one does cover up the left end of the panel.

---

### Post by corncob on 2011-01-11
> **corncob said:**
> I've plugged an external monitor into my Gateway NV54 running Maverick and its working fine except that there are boxes in the upper left corners.  One says "Laptop" and the other says "ViewSonic Corporation 19".  I know which monitor is which so I'm wondering if there is any way to remove them?  The one does cover up the left end of the panel.

Problem fixed itself.  Rebooting does wonders sometimes.

---

### Post by cfreak2399 on 2011-03-12
Having the same problems. Unfortunately nothing I've done so far has solved it.

ATI Radeon 5450. Duel Monitor working before upgrade. Same config now I just get a message that says "X does not support the requested size" and I get dropped into clone mode.

Reinstalled fglrx, rebooted countless times. Mucked around with Xorg.conf ... no matter what it's like it doesn't accept any new settings and it just reverts to the cloned display. I guess I'll have to downgrade to Lucid ... or get a different distro (what a pain)

---

### Post by oakbox on 2012-01-04
The solution of possibarendless worked for me.  Making the change in the ATI command center, rebooting, and THEN fiddling with gnome's monitor tool solved the problem for me.

- Richard

---

