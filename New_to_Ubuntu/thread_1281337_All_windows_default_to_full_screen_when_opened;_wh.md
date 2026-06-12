---
title: "All windows default to full screen when opened; where do I change this?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by hovzio on 2009-10-03
Hi,

 I am running Jaunty NBR in desktop mode on my eee1000h. Like mentioned in the title, my problem is that *any window whatsoever is being opened to fullscreen automatically as soon as opened; it will first open to its normal size and then jump to fullscreen. ( That really is with ANY window, even the littlest status bar for copying files will fill up the entire screen... really disturbing.) I am running compiz, although I think it was also doing this before activating compiz. I have spent quite a bit of time looking through compiz settings with no luck. I assume its a gnome setting somwhere deep inside gnome's config editor.. I cannot find it:(  I have googled but really haven't been able to find anything. As I said I am running gnome in its normal mode, not in the "remix mode" or whatever its called. Im greatfull for any links or help pointing in the right direction, thanks!  :)

---

### Post by tarps87 on 2009-10-03
I blieve that is done by a program called Maximus, you can try stopping it running
```
sudo killall maximus
```
If this work you can then remove it from the start up list or if you don't plan on using the remix mode you can uninstall it

---

### Post by Paqman on 2009-10-03
That should be "maximus", not "Maximus", btw.

It's designed to help you make best use of your small screen. If you don't want it running, then go to Startup Applications and uncheck it from the list, so that it won't start up again when you next boot.

---

### Post by hovzio on 2009-10-03
hi, thanks for the quick reply. :) Maximus is indeed the problem..somthing interesting thoe:

 I did a sudo killall and it didn't work. pgrep then said theres still a process, so kill -9 6547 then returns an exit status of 0. Cool... but the window still doesn't open properly. Then pgrep returns a new process.. Just for curiou sities sake, why is this process automatically restarting on its own? I've also noticed similar behavior with nautilus.. Nevertheless, removing it from gnomes startups expectedly works. :) Thank's tarps87 and Paqman!!!

---

### Post by tarps87 on 2009-10-03
> **Paqman said:**
> That should be "maximus", not "Maximus", btw.

It's designed to help you make best use of your small screen. If you don't want it running, then go to Startup Applications and uncheck it from the list, so that it won't start up again when you next boot.

Good point, fixed the post.

(stupid copy paste :))

> **hovzio said:**
> hi, thanks for the quick reply. :) Maximus is indeed the problem..somthing interesting thoe:

 I did a sudo killall and it didn't work. pgrep then said theres still a process, so kill -9 6547 then returns an exit status of 0. Cool... but the window still doesn't open properly. Then pgrep returns a new process.. Just for curiou sities sake, why is this process automatically restarting on its own? I've also noticed similar behavior with nautilus.. Nevertheless, removing it from gnomes startups expectedly works. :) Thank's tarps87 and Paqman!!!

I presume it was decided it was an important process for the remix, the same as GDM will restart if you kill it or something kills it.

---

### Post by Paddy Landau on 2009-10-03
If you don't like the Remix screen, then change to the standard Ubuntu desktop mode.

Preferences > Switch Desktop Mode

---

