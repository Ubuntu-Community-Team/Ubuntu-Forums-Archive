---
title: "images with transparency look funky when set to panel bar."
date: 2010-06-23
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-23
Any suggestions? I have libpng12-0 and I was looking through the other things, but none of them seem like they'd help me. It's no big deal if you can't help.

---

### Post by bwallum on 2010-06-23
I'm not sure what you mean. Could you perhaps expand on the issue?

---

### Post by warfacegod on 2010-06-23
Or post a screenshot?

---

### Post by Legendary_Bibo on 2010-06-23
Oh yeah I guess that would help. Well one of them was supposed to be blue going into a transparent background. The other is supposed to be a completely transparent image. There's an option to just make it a solid color with an opacity slider bar, but that doesn't seems to make it transparent at all. I think it's a filed bug though.

---

### Post by warfacegod on 2010-06-23
I know someone that might be able to help. I'll send a PM.

---

### Post by Legendary_Bibo on 2010-06-23
> **warfacegod said:**
> I know someone that might be able to help. I'll send a PM.

Okay, thanks :D

---

### Post by dzon65 on 2010-06-24
I supose that's still the lx panel?What theme?
edit:Let me rephrase.I guess you want it to be transparent?If it's a gtk theme,you could add this to the theme's rc #include "whatever is used for the panel".Could be in theme's rc or could be a seperate rc for the panel.However,not too many can be made fully transparent.You might have to do some changes to the jpg's used for the panel with gimp.
If you already did,there's a mistake with the color definition in the theme rc.Color definition mistakes tend to color purple/pink.

---

### Post by Legendary_Bibo on 2010-06-24
> **dzon65 said:**
> I supose that's still the lx panel?What theme?
edit:Let me rephrase.I guess you want it to be transparent?If it's a gtk theme,you could add this to the theme's rc #include "whatever is used for the panel".Could be in theme's rc or could be a seperate rc for the panel.However,not too many can be made fully transparent.You might have to do some changes to the jpg's used for the panel with gimp.
If you already did,there's a mistake with the color definition in the theme rc.Color definition mistakes tend to color purple/pink.
Yeah I found the documentation on Lubuntu's site. It's a bug that they're trying to fix.

---

