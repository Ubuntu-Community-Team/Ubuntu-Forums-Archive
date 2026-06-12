---
title: "firefox display problem, help please"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by bittergourd on 2009-07-20
since sometime my firefox couldn't display webpages correctly.  i have tried ff 3.5 and it doesn't help.  epiphany is working just fine, and i haven't installed or tried other browsers.  disabling all addons didn't help.  i am on jaunty btw.  listed below are some typical results.

i think it may be caused by some ff settings, but i just don't know where the problem could be...

any help please?

---

### Post by bittergourd on 2009-07-20
and also, in the error console, i got a bunch of warnings and errors like "_blahblah is not defined" and "Unknown property 'blah'. Declarations dropped" etc etc.

---

### Post by BinaryFeast on 2009-07-20
Based on those images it looks as if javascript may be turned off in the settings. But that's all I can think of.

---

### Post by SaaTeeVaaGreen on 2009-07-20
i wouldnt worry too much about the errors in the error console, i get loads of them as well. have you tried running ff from the terminal? this may give you some more useful error messages. also, wot sort of Internet connection/speed do you have? it looks a bit like ff just hasnt finished loading the pages.

---

### Post by BinaryFeast on 2009-07-20
By the way, try creating a new profile using 

```
firefox -P
``` 

(I believe that is the command to get to the profile manager.) That should make it possible to try out firefox with all the default settings.

---

### Post by SaaTeeVaaGreen on 2009-07-20
in ff go to edit>preferences and choose the content tab. are both java settings selected, and is the load images automatically option selected? if not, try selecting these.

---

### Post by bittergourd on 2009-07-20
thanks guys, but i found the solution.  apparently i cleared the cache and everything restores to normal.  no idea how cache messed up with the new webpages, but it's something good to know...

thank you guys again~~:D

---

