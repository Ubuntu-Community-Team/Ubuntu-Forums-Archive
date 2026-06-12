---
title: "firefox not working internet connection is on"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Ad88Ab99 on 2009-05-12
using firefox 3.0.10 and ubuntu 9.04
i have  internet connection
why is firefox not working help anyone

---

### Post by frup on 2009-05-12
is the offline mode ticked?

---

### Post by lynnevan on 2009-05-12
I have same problem and work offline is not ticked.  Left and right arrows and refresh and stop are all 'greyed' out.  When opening firefox, no page loads although it is set to open here:  [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326).  Also, xmarks should work and doesn't.  Never manages to connect.  If I put an address in the address bar, it will go there, but still no automatic loading at start and buttons greyed out.
Any ideas other than uninstalling all firefox stuff and reinstalling?

Thanks in advance,

lynnevan

---

### Post by freak42 on 2009-05-12
buttons are greyed at the beginning.
are you sure your homepage is still set in the ff settings?

---

### Post by lynnevan on 2009-05-12
Absolutely!!  I'm on it right now and the back and forward buttons are greyed and so is the refresh and stop.  The address bar is also blank and I just clicked on the link from gmail.  I'm running 9.04 x64 but that shouldn't make any diff.  I'm clueless!!

---

### Post by lynnevan on 2009-05-12
If I click the 'home' button, which is NOT greyed out, it brings up [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) w/o putting anything in the address bar.

Cool, huh?

---

### Post by Dill on 2009-05-12
Note that the .mozilla directory contains all of your profile information, and while deleting it might solve your problem, you should probably back it up if you have any bookmarks, etc. that you'd like to keep. 

Alternatively, a safer approach would be to try and create a new profile using the Profile Manager:

```
firefox -profilemanager
```

---

### Post by lynnevan on 2009-05-12
> **Ellen2 said:**
> You may like to try by fixing/removing the .mozilla directory, and start up firefox again. This I read somewhere when searching for a similar kinda issue.

I'm not sure why, but I ran sudo firefox and it worked fine, so I did as ellen2 suggested - deleted /home/usrname/.mozilla.  Restarted firefox, installed xmarks and no more problems.

Thanks all.

lynn

---

