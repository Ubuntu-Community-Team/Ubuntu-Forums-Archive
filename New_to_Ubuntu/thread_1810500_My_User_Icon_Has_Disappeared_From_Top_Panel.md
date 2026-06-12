---
title: "My User Icon Has Disappeared From Top Panel"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-07-23
Hi all,

Yesterday I loaded Glipper (Which I couldn't find afterwards). Today after a number of hours browsing, I noticed my user Icon was missing from the top right hand corner of the Classic top panel. It had been replaced with the Glipper Icon. I removed Glipper via Synaptic however the user icon is still missing from the panel. At present the Network Icon is in the right hand side of panel.

Could I have suggestions please about how I can restore the user Icon to its correct position?

Thank you,  :)i

---

### Post by westie457 on 2011-07-23
> **aussiebean said:**
> Hi all,

Yesterday I loaded Glipper (Which I couldn't find afterwards). Today after a number of hours browsing, I noticed my user Icon was missing from the top right hand corner of the Classic top panel. It had been replaced with the Glipper Icon. I removed Glipper via Synaptic however the user icon is still missing from the panel. At present the Network Icon is in the right hand side of panel.

Could I have suggestions please about how I can restore the user Icon to its correct position?

Thank you,  :)i

Copy and paste this ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

``` into a terminal.

Instant reset to system defaults for the panel.

---

### Post by OldBoy44 on 2011-07-23
So simple when you know how!

Many thanks, westie457!  That is one I will remember - :popcorn:

Cheers,  :)

---

