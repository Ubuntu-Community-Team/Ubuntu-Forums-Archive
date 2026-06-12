---
title: "[SOLVED] Firefox jumping to full-screen"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by kdm on 2008-12-04
Hi,

I am having a really annoying problem with firefox at the minute.
Whenever I have it minimized and then maximize it again, it automatically jumps to fullscreen mode and I can only get it back by pressing F11.  
I can't for the life of me find the setting to turn this off (if there is one).  Anyone else know?

Thanks

---

### Post by Michael.Godawski on 2008-12-04
Are you using compiz? Switching it off helped me with this issue.

---

### Post by sydbat on 2008-12-04
Yup...turning Compiz off should help.

---

### Post by binbash on 2008-12-04
go to CompizCOnfig settings manager (system > preferences) , then go to general options tab, and untick(or tick if it is unticked) unredirect fullscreen windows.

Also go to workarounds plugin and disable fullscreen legacy support

---

### Post by kdm on 2008-12-04
Not using compiz (AFAIK - Its not installed by default is it ?) but it is on a netbook if that makes a difference,

---

### Post by kdm on 2008-12-07
OK, thanks for the help - it looks like it was a problem with Compiz afterall, and here is how I solved it...

First I went to...

[B]System > 
Preferences >
CompizConfig Settings Manager >
Workarounds >
General>[/B] 
and then I Un-Checked "**Scale Window Title Filter**"

and that seems to have done the trick.

---

