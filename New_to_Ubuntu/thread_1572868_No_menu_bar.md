---
title: "No menu bar"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by Reggieee on 2010-09-11
I just installed Ubuntu 10.4.1 desktop i386 and when I restarted the machine (PIII Dell Optiplex GX110) there was no top menu bar. All I can see is the desktop image. I right clicked to change the desktop....that worked. So I do see the contextual right click menu but that is all. 

I messed around with the monitor settings to be sure that it just wasn't being seen on the screen but no luck. Is my machine just too old? If so what version can I run?

Thanks.

---

### Post by S.R on 2010-09-11
KDE or Gnome?

---

### Post by Miljet on 2010-09-11
You say there is no top panel, but do you have a bottom panel?

If your computer booted all the way to the desktop, I would say that your computer is quite capable of running Ubuntu.

---

### Post by Reggieee on 2010-09-11
Gnome. And I have no panels - top or bottom.....just a pretty desktop picture. That is all.

---

### Post by borth92 on 2010-09-11
[FONT=Arial Narrow]try this: **rm -rf .gnome .gnome2 .gconf .gconfd .metacity**[/FONT]

---

### Post by Reggieee on 2010-09-11
That worked! It looked like nothing happened but when I rebooted both the top and bottom bars where there.

I had to do figuring out how to put that in. 

Alt F2

Thanks

---

