---
title: "How can I stop Ubuntu from beeping my PC speaker?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Vunutus on 2009-02-17
It's extremely loud and extremely annoying. So many times when working with a console and such, any time I hit backspace too many times or try to tab complete something that doesn't have a match, my PC speaker emits an ear splitting beep.

How can I stop this short of removing the PC speaker?

---

### Post by gettinoriginal on 2009-02-17
I don't know for sure, but possibly check System, Sound, Sounds tab, and uncheck "play alert sound"

---

### Post by adult swim on 2009-02-17
instead of removing the speaker, you can do the next best thing and make it like its not even there.  to do this open up a terminal, applications>accessories>terminal, and type in ```
sudo modprobe -r pcspkr
```  then hit enter, type in your password, and hit enter again.  next type in ```
gksudo gedit /etc/modprobe.d/blacklist
``` and when the new window opens up, scroll down to the very bottom and add a line that says ```
blacklist pcspkr
``` now save and close the file.  you should never hear that terrible beep again!

---

