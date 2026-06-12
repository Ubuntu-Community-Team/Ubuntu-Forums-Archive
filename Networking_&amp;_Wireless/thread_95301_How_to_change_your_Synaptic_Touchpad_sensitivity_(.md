---
title: "How to change your Synaptic Touchpad sensitivity (solved!, but gnome dev questions)"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by Florian Hufsky on 2005-11-26
Hello,

i guess there are _A_LOT_ of people who might see this helpful: I have added a Wiki page on how to change the synaptic sensitivity.

It needs some redoing, but it's there nonetheless: [https://wiki.ubuntu.com/SynapticsTouchpadHowto](https://wiki.ubuntu.com/SynapticsTouchpadHowto)

It basically comes down to this:

1. Add sensitivity settings in xorg.conf
2. restart xserver (everytime you changed the settings).


I feel the possibility to 1. change the touchpad settings via a gui and 2. don't restart the xserver everytime is *critical* if ubuntu wants to have *any* success on laptops, thus:

**i'd like to write a graphical configuration utility for gnome to change the touchpad settings.**
but not something like qsynaptics. something *integrated in gnome* (like the mouse settings utility)

Could anybody give me a hint on:

1. how to write a programm that resides in the gnome settings menu
 (or b) how to edit the gnome mouse utility to add touchpad support)
2. how to change xorg configuration variables -on-the-fly- (i guess the mouse setting manager already does this).
3. how to get this into the next gnome release.


Don't worry, i'll edit the wiki text once i calmed down.

Huge thank in advance,
Florian

---

### Post by twisted_steel on 2005-11-26
I just wanted to add another site with synaptics configuration: [here]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad").

For changing settings dynamically, I imagine you would either need to call or integrate synclient, which allows you to pass settings to the driver as a normal user. In order to do this, the "SHMConfig" option must be set to "on" in your xorg.conf. According to the man page, "all local users can change the parameters at any time." You may want to take a look at the code for qsynaptics, which while I imagine is written in C++ rather than C, should give you some idea.

The code for the mouse configuration utility that comes with gnome is available at: [http://ftp.gnome.org/pub/gnome/sources/control-center/]("http://ftp.gnome.org/pub/gnome/sources/control-center/")[SIZE=-1]. 2.12 should contain the latest stable release, and 2.13 should contain the latest unstable version. If you want to look at the latest code, your best bet is to look at CVS. There is a [developer guide]("http://developer.gnome.org/tools/cvs.html") that should help get you started, or you can browse it [online]("http://cvs.gnome.org/viewcvs/gnome-control-center/capplets/mouse/").

Hopefully this will help :)
[/SIZE]

---

### Post by Florian Hufsky on 2005-11-26
Great - thanks. I'll give it a try.

---

### Post by mindwarp on 2005-11-28
Reverted your supposed "constructive" wiki editing.  Lets not act like we are 5, if you can't help then don't mess up what was already established.

---

### Post by Florian Hufsky on 2005-11-28
What was established wasn't helpful either (for breezy users). I'm going to clean the article today.

---

