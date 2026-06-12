---
title: "openbox autostart"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by dzon65 on 2010-04-25
What are the wright commands to add to the autostart file to automatically load conky and,say,gnome-panel at a openbox session start-up?
I first added conky to autostart like this:conky &.........didn't work.Than I added it like sleep4;conky &.......no go.I added both conky and panel to my obmenu and works without a problem.Perhaps it's due to the fact that this is a minimal gnome install using OB as windowmanager.So,this prob is in a openbox session.

---

### Post by arochester on 2010-04-25
See [http://urukrama.wordpress.com/openbox-guide/#Autostart](http://urukrama.wordpress.com/openbox-guide/#Autostart)

---

### Post by kerry_s on 2010-04-25
are you putting it in ~/.config/openbox/autostart.sh ?

---

### Post by dzon65 on 2010-04-25
> **kerry_s said:**
> are you putting it in ~/.config/openbox/autostart.sh ?

Yeah,it's working now,had to reboot.So,conky and panel's working.Only nitrogen opens empty.Added it to the autostart.sh but fails to "remind" where the wallpapers are located.
I managed to set my wallpaper with nitro,but each time I open it,it's empty.
This is what I added to autostart:nitrogen --restore &

---

### Post by kerry_s on 2010-04-25
my guess would be the nitrogen command in your menu, i'm assuming your just using "nitrogen" instead of "nitrogen /path/to/pics"

---

### Post by dzon65 on 2010-04-25
> **kerry_s said:**
> my guess would be the nitrogen command in your menu, i'm assuming your just using "nitrogen" instead of "nitrogen /path/to/pics"

Yep,that did the job.Thanks

---

### Post by Mark76 on 2010-04-25
nitrogen --restore &

---

### Post by dzon65 on 2010-04-25
Thanks for all the replies guys but I got it working.
Kind regards,J.

---

### Post by Mark76 on 2010-04-25
You need to add my line to your autostart.sh if you want the same wallpaper each time.

---

### Post by dzon65 on 2010-04-25
I know,it's done.Same with conky and the gnome panels,thanks.

---

