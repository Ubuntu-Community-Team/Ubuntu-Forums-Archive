---
title: "Time disappearing in Gnome &quot;Clock&quot; panel?"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by nosehat on 2010-10-05
Hi--

This is a minor annoyance, but I'm a newish user and I can't seem to figure out how to fix it.  Occasionally (I'm not sure what causes it), the area where the time is supposed to be displayed in the gnome clock panel gets covered up with a second version of the date.

See attached screenshot.

It's Clock 2.30.2, and Gnome Panel 2.30.2 if that helps.

Any ideas?

Thanks!

---

### Post by mcduck on 2010-10-06
That seems to be a fairly common bug in the indicator applets. I'm not aware of any actual fix to it, but simply reloading the panel when that happens (pres Alt-F2 and run "killall gnome-panel" will usually get everything to work correctly.

---

### Post by nosehat on 2010-10-06
Thank you, Mcduck, that does reset the panel.

Unfortunately, it also clears off any various buttons put on there by running applications (like the button vlc media player puts there, or the truecrypt button you can see in the screenshot).  

Perhaps there isn't a perfect solution at this point.  I wonder if the problem is inside the gnome panel, or if it's caused by applications not playing nice with the gnome panel.

---

### Post by mcduck on 2010-10-06
All the notification icons will appear again as soon as the program that put them there updates it's icon. Of course that won't help a lot if you are using notification icons for apps that don't actually use the icon to tell you anything, so the icon never reloads..

I'd say the problem is in the Indicator Applet & Indicator Applet Session. Gnome-panel has had similar rendering issues in previous versions but they seemed to get fixed some versions ago. And this problem appeared when the new Indicator applets were introduced. Also it never happens on other panels than the one with these applets, and usually only affects the area around the Indicator applets... (of course the bug *could* still be in the panel itself, and only appear with indicator applets, so I'm just guessing here. :D)

---

