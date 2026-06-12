---
title: "Previously reset my keybd repeat rate...now Ubuntu updates have disabled the change"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by thane1 on 2009-03-27
After having all I could take of not being able to slow down my keyboard repeat rate, I added the following line to my /etc/rc.local file, which fixed the problem [COLOR="DarkRed"]kbdrate -r 10 -d 500[/COLOR] .  All was well until new Ubuntu system updates were done.  At some point the kbdrate change has been disabled (by what I don't have a clue) and I'm back to no control over the rate.  Have seen a reference to doing the following, which might help [COLOR="DarkRed"]Temporarily add the following to your xorg.conf:
Section "ServerFlags"
Option "AutoAddDevices" "off"
EndSection

Restart X, and you will be able to change the settings. Once changed, you can remove those lines from your xorg.conf (which is recommended since setting AutoAddDevices to off can interfere with your keyboard)[/COLOR] .
Unfortunately again it seems Ubuntu has shifted a lot of what I recall was once found in my xorg.conf file to some other area.  I cannot find Section "ServerFlags" anywhere.  Using 8.10 amd desktop 64 and have all of the latest updates installed.  Thanks.

---

### Post by cariboo on 2009-03-27
If that will fix your problem, I would just add the three lines to the bottom of /etc/X11/xorg.cong. I have to do the same to be able to use Ctrl-Alt-Backspace in Jaunty eg:

```
Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

Jim

---

### Post by thane1 on 2009-03-28
Jim;
     Added the xorg.conf lines and was able to then reset my cursor speed.  Still cannot make repeat rate as slow as I had gotten it, when the rc.local edit still worked, but its somewhat better.  Would be nice though to get it a bit slower, so that I can "speedread" scrolling newsletter headings.  Hopefully this gets fixed soon.  Cheers.

---

