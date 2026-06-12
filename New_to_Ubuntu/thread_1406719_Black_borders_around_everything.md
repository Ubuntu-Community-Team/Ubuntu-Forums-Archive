---
title: "Black borders around everything"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by GL541 on 2010-02-14
Hi,

I installed a few new programmes last night, all from Ubuntu Software Center. The next time I switched on the computer, I saw thick black borders around windows, menus, desktop icons and even a border around the whole desktop (i.e. the black line between my background picture and the panel).

I also tried watching a video and it was very jumpy, especially when on fullscreen.

I have since uninstalled all the new programmes and run Computer Janitor but the problems persist.

Here's a screenshot

[http://i46.tinypic.com/wusd8m.png](http://i46.tinypic.com/wusd8m.png)

I'd be grateful of any advice. :)

---

### Post by GL541 on 2010-02-14
Right, so I've possibly fixed it.

I changed the appearance options [System > Preferences > Appearance, Visual Effects tab: selected "None"]. The borders disappeared. When I changed it back to "Normal" a box popped up saying "Searching for availible drivers" and, when the changes were effected, the borders re-appeared.

So I've put it back to "None" and now everything is working. Videos are perfect too.

So what happened? Have I lost some drivers? Will I need them again? Can I get them back?

---

### Post by kio_http on 2010-02-14
Could you state _what_ packages you installed?

This seams to be a driver or windows manager problem

---

### Post by coffeecat on 2010-02-14
By enabling visual effects you were enabling compiz, and the "searching for available drivers" message sounds as though the system was enabling a proprietary video driver. This sounds like an issue (bug) somewhere between compiz, your video chipset (I'm guessing ATI) and the video driver.

Post details of your video card and which driver you are using. What does it say in System > Administration > Hardware Drivers?

---

### Post by fluppet on 2010-03-01
I'm having exactly the same issue.

I installed gAlan using the Ubuntu Software Center, and then removed it. I also installed csound using Synaptic. After I restarted there were black boxes around all windows and performance was noticeably degraded. I removed all of the packages that were installed with csound and restarted, but still same problem. Turning off visual effects removes the black boxes, but that is not a satisfactory solution. Re-enabling visual effects brings up a dialogue box saying it is searching for drivers and then when it is finished I have the black boxes again, as reported by OP.

I'm using a Toshiba Satellite A200-13O.
Xorg.0.log reports:
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3

Thanks

---

