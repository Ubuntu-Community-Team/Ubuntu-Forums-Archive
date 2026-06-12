---
title: "Emerald and Appearance Preferences conflict"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by aLgorhythmic on 2010-01-05
Hi, I was browsing the Ubuntu Software Center and I found out about Emerald. I looked it up, installed it, and downloaded some themes. I then found out I needed CompizConfig Settings Manager for the theme to take effect. Before I found out about Emerald, I was already customizing my laptop's appearance with what were pre-installed.

My problem is: Only the title bar and the icons(close, maximize, minimize) are changed. The Controls(System>Preferences>Appearance>[Some Theme]>Controls) are not affected(window body background, scroll bar, etc.) and still remain the same as to what I have selected before. I already did some searches, restarts, downloads and still no effect. 

I'm using Ubuntu 9.10 and am a complete newbie with regard to Linux OS's. 

Thanks.

---

### Post by oldos2er on 2010-01-05
> **aLgorhythmic said:**
> My problem is: Only the title bar and the icons(close, maximize, minimize) are changed. The Controls(System>Preferences>Appearance>[Some Theme]>Controls) are not affected(window body background, scroll bar, etc.) and still remain the same as to what I have selected before. 

Working as designed. Emerald works only on layouts of buttons, look, title bars and frames.

---

### Post by aLgorhythmic on 2010-01-05
> **oldos2er said:**
> Working as designed. Emerald works only on layouts of buttons, look, title bars and frames.

Oh I see. I kinda thought it would be like that.. Thanks. Anyways, how do I make the others transparent? The given themes were solid colors, and when I browsed for themes online (I clicked the link that was on the Appearance Preferences) the themes were in solid colors. I was just able to make my Terminal transparent / translucent which was a little progress for me, but still no luck with the windows.

---

### Post by Methuselah on 2010-01-05
To change your window interior theme you need to look for GTK 2.0 themes that you like.

---

### Post by mcduck on 2010-01-05
> **aLgorhythmic said:**
> Oh I see. I kinda thought it would be like that.. Thanks. Anyways, how do I make the others transparent? The given themes were solid colors, and when I browsed for themes online (I clicked the link that was on the Appearance Preferences) the themes were in solid colors. I was just able to make my Terminal transparent / translucent which was a little progress for me, but still no luck with the windows.

GTK doesn't yet have proper support for transparency (although there are already some hacks that allow it). So you are not going to find any themes with transparency.

Applications themselves of course are able to use transparency (At least as long as you have some compositing manager, like Compiz, running), but that comes from the application itself, not your GTK theme.

---

### Post by aLgorhythmic on 2010-01-05
> **Methuselah said:**
> To change your window interior theme you need to look for GTK 2.0 themes that you like.

Hi, I looked up GTK 2.x themes and I downloaded some. I browsed through the contents and I found metacity folder, gtk 2.0 folder, a .tat.gz file and a .emerald file. How do I install this?

Thanks.

EDIT: I was able to figure it out. It seems that the System>Preferences>Theme was at System>Preferences>Appearance.

---

