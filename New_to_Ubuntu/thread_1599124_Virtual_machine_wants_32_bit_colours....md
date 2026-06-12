---
title: "Virtual machine wants 32 bit colours..."
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Crazychicken on 2010-10-17
That's what it says. is there any way to appease it so I can run 3d games on my windows virtual box?

System-Preferences-Display isn't there.

---

### Post by sikander3786 on 2010-10-17
On the main page of Virtualbox, select your machine and click 'Setting'. You will find 3d under Graphics. Enable it from there.

All the virtual servers don't give the guests full access to the graphics card, it is only a virtual graphics card so the performance might be a little choppy.

---

### Post by Crazychicken on 2010-10-17
well, i found an option to enable 3D accelleration, but not to change the display. I can change to 16 bit within the virtual "Windows" but the thing keeps warning me it's "optimized for 32 bits"


How do I get Ubuntu itself to go from 16 to 32 bits (or 24 as they say on other threads)?
I can't find instructions for the more recent versions of Ubuntu.

---

### Post by sikander3786 on 2010-10-18
You can see these results from virtualbox community.

[http://www.google.com.pk/search?hl=en&safe=off&client=firefox-a&hs=EMl&rls=org.mozilla:en-US:official&q=+site:forums.virtualbox.org+virtualbox+ubuntu+guest+32+bit+colours&sa=X&ei=Pv67TIy-G43QcbTHpeMM&ved=0CBoQrQIwAA](http://www.google.com.pk/search?hl=en&safe=off&client=firefox-a&hs=EMl&rls=org.mozilla:en-US:official&q=+site:forums.virtualbox.org+virtualbox+ubuntu+guest+32+bit+colours&sa=X&ei=Pv67TIy-G43QcbTHpeMM&ved=0CBoQrQIwAA)

---

### Post by Crazychicken on 2010-10-18
I added the lines

DefaultDepth 24
SubSection "Display"
Viewport  0 0
Depth     24
Modes     "1024x768"
EndSubSection

to the xorg configuration file, it worked as it doesen't give me the error anymore but the resolution is horribly wrong.
The program I wanted to fix didn't work anyway, so I'm giving up.

---

