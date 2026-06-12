---
title: "Problem with Firefox"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by audine on 2009-03-18
I've been running Ubuntu for weeks now with little or no problems, but ... 

Something strange has happenend recently to Firefox -- the close, minimize and maximize icons are gone, they were there before.  Now when I want to close my browser I have to use the quit option under File, or I can use View>Full Screeen and the close, minimize, maximize icons are there, but I don't like using full screen.  Also when Firefox is open it covers the bottom part of the screen where I have the option to switch to another desktop or minimize the open windows and be at the desktop. Any suggestions?

Thanks for the help,
Audine

---

### Post by stoogiebuncho on 2009-03-18
Sometimes pressing F11 twice is all you need.

You can also try pressing Alt+F2 and entering
```
compiz --replace
```

---

### Post by fooman on 2009-03-18
try this:

open firefox and and press the f11 key *twice* to get to a normal size screen.

click on the unmaximize button.

close firefox....then open firefox.

click the maximize button.

problem should be gone.

---

### Post by audine on 2009-03-18
> **stoogiebuncho said:**
> Sometimes pressing F11 twice is all you need.

You can also try pressing Alt+F2 and entering
```
compiz --replace
```

Thank you! Pressing F11 worked except I would lose the setting each time I re-opened Firefox.  I did Alt+F2 and entered the code -- and it worked.

---

### Post by LowSky on 2009-03-18
Compiz has a setting that will fix this issue to never annoy you again

go to CCSM > Workarounds > legacy support

I think....?

sorrry things changed in 9.04 and I cant remember details

---

### Post by phantom3113 on 2009-03-18
installing the package "fusion-icon" gives you a small daemon in the upper-right bar that makes controlling those kind of things (window decorator, window manager) a little easier. You'll need to add it to sessions for it to start up on boot, but that's pretty easy to do :)

---

### Post by jordanae on 2009-03-19
You could always try Ctrl-Q

---

### Post by joneez on 2009-03-23
> **fooman said:**
> try this:

open firefox and and press the f11 key *twice* to get to a normal size screen.

click on the unmaximize button.

close firefox....then open firefox.

click the maximize button.

problem should be gone.

That worked perfectly, thanks!!
There seem to be some websites that change this setting to throw up full screen pop-ups. It's extremely annoying!

---

