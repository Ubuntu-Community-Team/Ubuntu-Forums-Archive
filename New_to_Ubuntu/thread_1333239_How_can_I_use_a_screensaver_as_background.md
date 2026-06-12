---
title: "How can I use a screensaver as background?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by KIAaze on 2009-11-21
I would like to have a screensaver as background image.
Apparently, this should be possible with xwinwrap, but I can't get it to work.
Tried:
[http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap)
and
[http://code.google.com/p/gwinwrap/](http://code.google.com/p/gwinwrap/)

None worked.
Is it even possible under KDE4 with Kwin?

---

### Post by frenchn00b on 2009-11-21
xlockmore can put on root

--onroot

---

### Post by KIAaze on 2009-11-21
What? :confused:

---

### Post by frenchn00b on 2009-11-21
> **KIAaze said:**
> What? :confused:

[http://linuxreviews.org/screenshots/tn/xscreensaver_in_root_window.png.index.html](http://linuxreviews.org/screenshots/tn/xscreensaver_in_root_window.png.index.html)
you can run xscreensaver screensavers in your root (desktop-level) window! Start them with the full path and -root & as parameter

or xlockmore can do it too
[http://gwyn.tux.org/~bagleyd/xlockmore.html](http://gwyn.tux.org/~bagleyd/xlockmore.html)

---

### Post by KIAaze on 2009-11-21
I tried:
```
/usr/lib/xscreensaver/glmatrix -root
```
and nothing happens...

I am running Kubuntu 9.10 with KDE 4.3.2.

---

### Post by frenchn00b on 2009-11-21
eventl try this... 

```
h
Rand=`expr $RANDOM % 10`
case $Rand in
	0) echo "xmatrix" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/xmatrix -root -small -delay 100000 -density 40 &
		;;

	1) echo "ripples" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/ripples -root -oily -light 2 &
		;;

	2) echo "xflame" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/xflame -root &
		;;

	3) echo "cynosure" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/cynosure -root &
		;;

	4) echo "coral" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/coral -root -delay 0 &
		;;

	5) echo "blaster" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/blaster -root &
		;;

	6) echo "starwars" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/starwars -root &
		;;
	
	7) echo "xrayswarm" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/xrayswarm -root &
		;;
	8) echo "whirlwindwarp" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/whirlwindwarp -root &
		;;
	9) echo "goop" > /var/local/gdm/back.dat
		/usr/lib/xscreensaver/goop -root -maxvelocity 0.6 -elasticity 0.9 &
		;;

esac

Obviously you can change which screensavers run as a background, and tweak the arguments passed to each of those, check your xscreensaver documentation for more info.
Put this in your /etc/gdm/PreSession/Default script

#!/bin/sh
# The following line was already in the script
# Don't add it if yours doesn't have this already.
/usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -l $DISPLAY $USER

# From here on relates to the dynamic background hack
Name=`cat /var/local/gdm/back.dat`
BPID=`pidof $Name`
kill $BPID


This will kill off whichever 
```

---

