---
title: "Synaptics touch pad virtual corner button config"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-17
Hey all,

I was wondering if anyone knows how to configure the virtual buttons that are available with a synaptics touchpad. I have a Toshiba laptop and in windows i loved using the corners of the pad as virtual buttons (top right for maximise bottom right for minimise etc...) there was a nice GUI for configuration in vista on this and i was wondering if anyone knew how to do it in ibex. I have looked around and haven't found much,

Thanks a lot in advance everyone!

---

### Post by Hospadar on 2008-12-17
You could try installing the compizconfig-settings-manager

I don't think you can do exactly the same thing, but you can set up screen corners (when you move the pointer to corner) to do any action in compiz.

As for tapping a part of the touchpad, I don't know of that

---

### Post by 11010110 on 2008-12-18
Thanks for the reply but i have tried that and it just aint the smae the ability to minimise windows and call up my most used programs regardless of the mouse cursor position is great for productivity and just a great feature. 

Any other ideas?

---

### Post by 11010110 on 2008-12-18
bump

---

### Post by kovan on 2009-04-23
I've wondered this one for a long time.

---

### Post by GreatMan(TM) on 2009-11-15
I always had the top right corner act as the middle mouse button for opening tabs. It was like that by default, so I was in trouble when I upgraded and it no longer behaved the same.

Anyway, this is how I fixed it: You need the gsynaptics package. From the command line you can use ```
synclient -l
``` to list the possible setting, most of which aren't in the GUI tool.

For corner buttons you want to edit the CornerButton lines. So all I had to do was enter ```
synclient RTCornerButton=2
```and I was able to tap the right-top corner button to emulate pressing the middle-mouse button.

Hope this helps

---

