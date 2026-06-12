---
title: "Screen distorted after changing resolution"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Mobyseven on 2009-11-25
Hi all,

I'm very new to Linux/Ubuntu, and am a bit lost with a problem. My display was looking stretched out, so I checked the screen resolution, found it was too high, and changed it to correct the problem. On doing so, my screen flickered as though it was going to readjust, but wound up instead coming back as a screen full of thin horizontal lines, distorting the entire screen. Rebooting didn't help, nor did loading a different kernel. The screen itself is fine (can get to text interface fine on startup) but am not sure what to do next.

A friend of mine had a quick look and mentioned something about xorg (which I've gathered is the program that communicates with the monitor), but we're in the middle of exams at the moment so he couldn't spend too long looking at it, so he recommended I ask here.

Has anybody else had this or knows how to fix it?

Cheers,

Rich

---

### Post by rolandixor on 2009-11-25
I've never had that particular problem, but a few things jump to mind. What graphics chip/card are we dealing with?

Can you use a text console (when pressing CRTL+ALT+F1)?

In any case, there is always the option to use the recovery mode to fix your X server, but with nvidia or ati graphics that would cause you to lose 3D acceleration unless you are on open source drivers.

---

### Post by jacobs444 on 2009-11-25
The first thing that comes to mind is that it is a refresh rate your monitor doesn't fully support, typically all lcds will support 60hz and 75 hz, the latter being my preference.

---

### Post by Mobyseven on 2009-11-25
1. Graphics card is NVidia. Not sure what driver I'm using.
2. Yes, I can use the text console, though as of yet I'm not sure how.
3. If it's the refresh rate, how can I fix that via text console? Exploring a bit now, but I'm wary to do anything I'm not sure of - don't want to be fixing two problems...

Cheers, also.

---

### Post by Mobyseven on 2009-11-26
Still no progress. Tried to figure out how to change resolution or refresh rate via the text console, but no luck. Help specifically with that problem might get me through to fixing the rest myself?

---

### Post by Mobyseven on 2009-11-27
Okay...figured out how to change stuff in xrandr, but didn't help - won't actually let me change refresh rate or resolution. Ctrl-Alt-Backspace didn't work either. Also tried moving .gnome2 to a new folder in the hope that on restart things would reset to sanity, but no such luck.

Any other ideas? I am lost adrift in a sea of Linux...

---

