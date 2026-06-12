---
title: "Tip for anyone with an Intel 943/940 Integrated graphics."
date: 2009-03-14
forum: New to Ubuntu
---

### Post by philinux on 2009-03-14
Found these options in this months Linux Format mag.
I was getting flickering madness on glxgears and rotating cube was juddery.

Now much smoother. Here's the xorg.conf tweak.

```
   Section "Device"
	Identifier	"Configured Video Device"
        Option          "AccelMethod""EXA"
        Option          "MigrationHeuristic""greedy"
        Option          "TripleBuffer""true"
```
 
Option 2 governs the amount of pixelmap data moved to video memory which is faster then ram.

Option 3 enables more efficient method of double buffering, removes flicker from a screen update.

Hope this hasn't been covered before.

---

