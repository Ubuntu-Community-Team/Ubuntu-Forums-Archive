---
title: "Application windows &quot;fly&quot; out of sight under compiz"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-03
hey everyone

i've noticed sometimes that when using compiz, especially with the "wobbly windows" effect enabled, windows will sometimes just "fly out of sight". this only happens when i'm moving the window. 

by "fly out of sight", i mean the program simply disappears. it no longer seems to be running at all. it's not even listed under system monitor. i also checked other desktops in the cube, hoping that it just moved to another desktop, but it's never there. 

any ideas/suggestions on what is causing this?

:confused:

---

### Post by Temposs on 2009-04-03
I think your wobbliness is too extreme.  You need to change the movement settings for wobbly windows so the movement isn't so extreme. You might also try turning on the Snapping Windows plugin.

---

### Post by Hospadar on 2009-04-03
DANGER: Wobblieness exceeding recommended limits!!! REDUCE WOBBLIENESS

Sorry, it just sounded funny how it was worded.

Anyways,
it might just be that those applications that are appearing to fly away are crashing and compiz is just trying to animate the window closing?  Is it just one application that disappears or all of them?  If just one maybe that's the issue.

Other than that, as mentioned above, maybe decrease wobblieness, or set compiz to minimum settings and slowly add plugins one at a time and see if you can narrow it down to a specific compiz plugin.

If you don't already, install "compizconfig-settings-manager" from synaptic, and you can then configure plugins individually at System->Preferences->Advanced Desktop Settings (i think it's called, it's right at the top, it's obvious)

---

### Post by asuastrophysics on 2009-04-03
yeah i thought it might just be compiz animating a crashing app, but if firefox crashes, doesn't it usually pop a window up on the next run saying "send error report" ? (at least earlier versions of firefox did this.

btw i just did a clean install of ubuntustudio and i was wondering why the compiz settings manager was missing from preferences...seems installing compizconfig from synaptic made it come back. thanks! ;)

under the wobbly windows plugin, i changed the "spring factor" from 10.0 to 5

hopefully that did the trick

---

