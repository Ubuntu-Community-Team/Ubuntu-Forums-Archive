---
title: "Logitech LX8 mouse back/forward buttons not working!"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by narmoture on 2009-04-17
As the title says, and HIDPoint is not working either. I have a Wave Cordless/LX8 keyboard mouse combo on 8.10 Intrepid, and the basics work, but I hate that the back/forward buttons don't work! 

I searched these forums and Google to see if there was anyway to map the buttons, but most of the guides went over my head or were outdated. Many talk about editing the xorg.conf, but apparently most settings in that file is now ignored(arrrg). I found somewhere that you could check your input devices with **xinput list --short  **, and this is what I got:

```
"Virtual core keyboard"	id=0	[XKeyboard]
"Virtual core pointer"	id=1	[XPointer]
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
"Logitech USB Receiver"	id=3	[XExtensionKeyboard]
"Logitech USB Receiver"	id=4	[XExtensionKeyboard]

```

(Macintosh mouse!? I have an old PC! Or is that just generic?)

Then the guide went on about checking the mapping and changing it, which is where I got totally lost. I'm guessing one of the "Logitech USB Receiver" devices is my mouse, since it's wireless. But how do I change the mapping? And btw, how do I know which buttons are assigned which number?

I would like someone to explain this mysterious process to me. Assume I'm a total idiot. Write like a 'for dummies' book. **Don't** tell me to use HIDPoint. It doesn't work. If someone would like to take a stab at explaining how to map extra keys on my Wave too, be my guest!

---

