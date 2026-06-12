---
title: "Is there a GUI for intel graphics controlers?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by powel212 on 2009-04-17
I have the nvidia x-sever settings GUi on my computer and it works great. But, I am trying to help my friend get "Extra" Desktop Visual effects and compiz and all these fun things running on his HP laptop. I can't find any kind of configuration tools for his intel based graphics adapter. We had compiz effects running on the initial install of iBex but after running updates we can no longer have the nice visual effects working.

Is there a GUi to configure intel graphics cards? Something like the nVidia x-server settings controller?

Any help is appreciated.

Powel

---

### Post by swoll1980 on 2009-04-17
There isn't a GUI. What's the chipset?

---

### Post by powel212 on 2009-04-17
I am unsure of the chipset. He has gone home now and taken his computer with him. So I can't get that information at present. 

No GUi. In this case I was thinking if I put in a live disk and get compiz running again maybe I can copy the xorg.conf out of the live  file system and copy it onto the hard-drive. Sound reasonable?

Powel

---

### Post by swoll1980 on 2009-04-17
> **powel212 said:**
> I am unsure of the chipset. He has gone home now and taken his computer with him. So I can't get that information at present. 

No GUi. In this case I was thinking if I put in a live disk and get compiz running again maybe I can copy the xorg.conf out of the live  file system and copy it onto the hard-drive. Sound reasonable?

Powel

just go to system>preferences>appearance click visual effects tab then select what level of effects you want. It should work. If not run ```
compiz --replace 
``` in the terminal, and post the error you get

---

### Post by powel212 on 2009-04-17
I will try that. Thank you.

Powel

---

