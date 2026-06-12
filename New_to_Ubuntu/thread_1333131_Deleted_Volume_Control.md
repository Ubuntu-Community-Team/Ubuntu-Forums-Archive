---
title: "Deleted Volume Control"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by rlogan on 2009-11-21
Hi all

My son deleted his volume control on the Ubuntu/Gnome desktop and I must admit I have only had a quick look at it, might have to have a better look. 

Has any got any suggestions how to get it back.

Cheers

Richard

---

### Post by camaron1 on 2009-11-21
> **rlogan said:**
> Hi all

My son deleted his volume control on the Ubuntu/Gnome desktop and I must admit I have only had a quick look at it, might have to have a better look. 

Has any got any suggestions how to get it back.

Cheers

Richard

On System>Preferences go to Startup Applications and tick Volumen Control

I think that should do

---

### Post by JBAlaska on 2009-11-21
Since you can't delete the volume control by right clicking on it, maybe he removed the indicator-applet that holds all of the system indicators. you can restore that by right clicking on the panel and adding it back with "Add to panel..."

---

### Post by 73ckn797 on 2009-11-21
> **JBAlaska said:**
> Since you can't delete the volume control by right clicking on it, maybe he removed the indicator-applet that holds all of the system indicators. you can restore that by right clicking on the panel and adding it back with "Add to panel..."


I was able to delete the volume control. One day there were suddenly 2 volume control icons in the top panel. I right clicked on one to remove and both disappeared. The add to panel feature would not restore the icon.

I performed the following in terminal:
```
gconftool-2 --recursive-unset /apps/panel
```I then restarted the system and the panels reappear with all standard icons. If you have placed any icons to launch other programs you will have to add those back manually by right clicking the program in the menus and selecting add to panel or desktop.

To the OP, I do not see whether the problem has been solved so I make my recommendation.

---

### Post by rlogan on 2009-11-28
Thanks for the replies everyone, they were appeciated !!!

I had tried the startup applications with no joy, likewise trying to add the applet back. In the latter there was no option for sound for some reason.

The suggestion to reset panels with

gconftool-2 --recursive-unset /apps/panel

worked like a charm !!!

My son is stoked to have his volume control

Lets see how long it takes for him to do something else like this..lol

Thanks heaps for your suggestions

Cheers

Richard

---

### Post by 73ckn797 on 2009-11-29
> **rlogan said:**
> Thanks for the replies everyone, they were appeciated !!!

I had tried the startup applications with no joy, likewise trying to add the applet back. In the latter there was no option for sound for some reason.

The suggestion to reset panels with

gconftool-2 --recursive-unset /apps/panel

worked like a charm !!!

My son is stoked to have his volume control

Lets see how long it takes for him to do something else like this..lol

Thanks heaps for your suggestions

Cheers

Richard

Great to see things have worked out. Enjoy!

---

