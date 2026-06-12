---
title: "[SOLVED] Google Earth Causing Laptop to Crash"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-12-04
hey, what's up? I had recently installed Google Earth through Terminal, but the program only makes my computer screen turn pitch-black, my mouse into an "x"-shape, and, later, static like on a TV without cable or an antenna.
Is there a solution to this?
Or would it be best to uninstall? How can I do this when it does not appear in the "Add/Remove Applications" window?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by glennric on 2008-12-05
How did you install google earth from the terminal?

Try 
```
sudo apt-get remove googleearth
```
in the terminal.

---

### Post by RedStarYellowSun on 2008-12-05
Here is how I did it:

"wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin) && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin"

I go that from [http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html) .

Thanks!

---

