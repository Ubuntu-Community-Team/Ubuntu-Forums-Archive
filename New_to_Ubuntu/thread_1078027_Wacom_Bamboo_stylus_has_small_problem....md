---
title: "Wacom Bamboo stylus has small problem..."
date: 2009-02-22
forum: New to Ubuntu
---

### Post by itissid on 2009-02-22
Hi,
I bought a new Bamboo tablet and set up for my Intrepid ibex using the directions on ([https://help.ubuntu.com/community/WacomTroubleshootinghttps://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshootinghttps://help.ubuntu.com/community/WacomTroubleshooting))...
The Xorg was done as said...Everything was ok, I had to just boot up X every time which was irritating... I did try to get the hotplugging option working thru HAL... But then was not satisfied since the eraser and pad buttons werent working... So decided to undo it...
When I reverted to Xorg I had a problem. I was not able to double click using the touch on the pad and the drag action across the pad was not working... I double checked in windows to make sure the tablet was not malfunctioning and it wasnt... Can any one tell me whats wrong?

Many thanks...

---

### Post by itissid on 2009-02-23
Bump... any one there?

---

### Post by itissid on 2009-02-25
thanks for the help... But I figured this out myself finally.. Seems like the Input section for "Synaptic touchpad" and wacoms "pad" in Xorg had the common word pad which was confusing X... That was fixed... So maybe this one some one can help me...
Unplugging when X is on makes the pad loose the functionality of proximity detection and the absolute mode changes to relative…(It becomes a dumb old mouse).. But stylus buttons and touch pad buttons are still working…. Is it possible to get those functionality without system restart or possibly x restart?? May be reload a module or somethng?

---

### Post by Favux on 2009-04-10
Hi itissid,

Try the old hotplug commands.  ctrl-alt-F1 and then ctrl-alt-F7.

---

