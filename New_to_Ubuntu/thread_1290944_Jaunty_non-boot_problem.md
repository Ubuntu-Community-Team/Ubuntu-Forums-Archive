---
title: "Jaunty non-boot problem"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by gremial on 2009-10-14
I've just started having booting difficulties, thus:

Switch laptop at home on as normal;
Login screen appears - login as normal;
Usplash screen runs as usual;
Screen blanks, outline of task bar appears, then NOTHING! Complete freeze - CTRL/ALT/BKSP does nothing. Only holding the power switch and removing the battery will have any effect. The only session into which the computer will boot successfully is failsafe terminal; failsafe Gnome freezes.

Earlier that evening I'd had a couple of instances where coming out of the screensaver had prompted an unexpected restart. I wondered whether this might be anything to do with the Jaunty/Intel integrated graphics chip issue; graphics performance hasn't been ideal since I upgraded to Jaunty.

I'm at a loss as how to proceed and any advice will be gratefully received!

---

### Post by gremial on 2009-10-14
As a post-script to my post above:

This page - [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) - looks promising, particularly "Problem: Freezes right after entering login credentials" and "Problem: Freezes occur when idle and screensaver is set to random settings or OpenGL" sections; the problems started occurring after switching to the 'Skyrocket' screensaver, hence the possible 3D/OpenGL implications?

I assume that I would select the Failsafe Terminal option and type:

sudo chmod a-x /usr/bin/compiz

and then whatever the command would be to boot as normal, if someone could please advise (if, indeed, I'm on the right track here?)

Thank you!

---

### Post by hal10000 on 2009-10-14
> I assume that I would select the Failsafe Terminal option and type:

sudo chmod a-x /usr/bin/compiz

and then whatever the command would be to boot as normal, if someone could please advise (if, indeed, I'm on the right track here?)

Yes you should do this and then type [COLOR="Red"]init 2[/COLOR] to resume a normal login

---

### Post by gremial on 2009-10-14
> **hal10000 said:**
> Yes you should do this and then type [COLOR="Red"]init 2[/COLOR] to resume a normal login

Thanks!

Would [COLOR="Red"]startx[/COLOR] be the wrong thing to use in this situation?

---

### Post by hal10000 on 2009-10-14
No, you can also use startx, but if you don't have a [COLOR="Red"].xinitrc[/COLOR] file in your home directory which starts your gnome-session (or kde or whatever) then yo'll just get a minimalistic window-manager

---

