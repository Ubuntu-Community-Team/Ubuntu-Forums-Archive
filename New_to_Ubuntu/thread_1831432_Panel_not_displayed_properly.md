---
title: "Panel not displayed properly"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by ashhab2010 on 2011-08-23
My top panel is not being displayed properly... i am not sure from when this started happening..
the Internet connection display, the about me thing and the shut down thing is not being displayed..
plz help ...
i hav attatched a screenshot of my panel

---

### Post by raja.genupula on 2011-08-23
restore your panel 
[http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

---

### Post by ashhab2010 on 2011-08-23
thanks.... it worked
but can u tell me why it happenend??

---

### Post by raja.genupula on 2011-08-23
honestly i too dont know . but i thinking as bugs .

---

### Post by ashhab2010 on 2011-08-24
the problem again appeared ....
the panel is sometimes displayed properly sometimes it isnt...
help plzzzz..

---

### Post by ashhab2010 on 2011-08-26
bump.........

---

### Post by raja.genupula on 2011-08-27
[http://ubuntuforums.org/showthread.php?t=883099](http://ubuntuforums.org/showthread.php?t=883099)

---

### Post by ashhab2010 on 2011-08-28
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=883099](http://ubuntuforums.org/showthread.php?t=883099)

didnt help!!!!

---

### Post by ashhab2010 on 2011-09-01
Big bump!!!!

---

### Post by westie457 on 2011-09-01
Try this in a terminal ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

If that does not work there is something else causing the issue.

---

### Post by Grenage on 2011-09-01
OP: You aren't alone;  I've seen this on my laptop, but it just stopped happening for no particular reason.  Here's the bug listing:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448)

Westie: You're not far away! :)

---

### Post by akoskm on 2011-09-01
There was a know bug ([https://bugs.launchpad.net/bugs/827673]("https://bugs.launchpad.net/bugs/827673")) in unity-2d which is already fixed, if you are on unity-2d simply update it.
Hope this helps.

---

### Post by westie457 on 2011-09-01
@ Grenage > Westie: You're not far away! 

Is that meant by a reply is close to the answer or our locations?

---

### Post by Grenage on 2011-09-01
Locations, naturally. :)

---

### Post by ashhab2010 on 2011-09-01
> **westie457 said:**
> Try this in a terminal ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

it works temporarily... after a reboot the problem appears back..


@ akoskm - im using gnome

---

