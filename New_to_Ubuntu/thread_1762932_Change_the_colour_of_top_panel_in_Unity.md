---
title: "Change the colour of top panel in Unity"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by DrShavargo on 2011-05-19
Hi everyone,

I'de like to know if there's a way to change the colour of the top panel in Unity. Not that I have anything against grey, but I'de love to have it black.

I'm running Natty 11.04.

Thanks in advance.

---

### Post by ExileAmongYou on 2011-05-19
Well, you can change it by changing your theme, but that will change the colours of all the window borders as well. Open up Appearance, go to the Theme tab and change it to see what I mean. If that's what you want, you can look on gnome-look.org for a theme that's dark enough for you.

---

### Post by DrShavargo on 2011-05-19
> **ExileAmongYou said:**
> Well, you can change it by changing your theme, but that will change the colours of all the window borders as well. Open up Appearance, go to the Theme tab and change it to see what I mean. If that's what you want, you can look on gnome-look.org for a theme that's dark enough for you.

Yeah, I figured. I've changed it a few times, but I'de still like to know if there's a way to only change the colour. :/
Thanks anyways for the advice.

---

### Post by DrShavargo on 2011-05-20
Bump. :P

---

### Post by satreth on 2011-05-20
Hi, 
Yes, there is a way to only change the color of the panel, but you probably have to edit the theme files manually.

To be a little more specific (Not really absolute beginner stuff), to change the panel's color to black for the "Ambiance" theme I had to edit the */usr/shared/themes/Ambience/gtk-2.0/apps/gnome-panel.rs* file. In it I had to replace the lines at the beginning, in the "panel" style from:
```

bg_pixmap[NORMAL] = "img/panel.png"
bg[NORMAL] = "#4b4a46"

```
to 
```

bg[NORMAL] = "#000000"

```
But the changes might get lost if the theme gets updated.

ciao

---

### Post by Larkspur on 2011-05-20
If that works, you could save it as a new theme, couldn't you?

---

### Post by satreth on 2011-05-20
Yes, that should be possible. You probably have to edit also the gtkrc and index.theme files of the copied theme to avoid conflicts with the original "Ambience" theme.

---

### Post by Larkspur on 2011-05-20
> **satreth said:**
> Yes, that should be possible. You probably have to edit also the gtkrc and index.theme files of the copied theme to avoid conflicts with the original "Ambience" theme.

Good point.  By the way, do you know if there's a part of the gtkrc file that can change the colour of the panel font only?

---

### Post by satreth on 2011-05-20
> **Larkspur said:**
> Good point.  By the way, do you know if there's a part of the gtkrc file that can change the colour of the panel font only?

Sorry, did not find anything.

---

### Post by Larkspur on 2011-05-20
> **satreth said:**
> Sorry, did not find anything.

Thanks for looking.:)

---

### Post by satreth on 2011-05-20
> **Larkspur said:**
> Good point.  By the way, do you know if there's a part of the gtkrc file that can change the colour of the panel font only?

Found it. You just have to add
```
text[NORMAL] = "#ff0000" 
```
just after the 
```
bg[NORMAL] = "#000000"
```
line added before

regards

---

### Post by Larkspur on 2011-05-20
Thanks!

---

