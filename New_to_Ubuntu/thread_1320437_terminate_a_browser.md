---
title: "terminate a browser"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by ryon341 on 2009-11-09
I have a problem with a browser that won't close.  This should be simple, but I can't figure it out.

I opened the website [https://eeroll.uhc.com](https://eeroll.uhc.com).  It's a site for my company. When I open it, a dialog box is create for login.  There is no way to close the dialog box or the underlying website.   I tried a hard reboot and the same site pops up on start.

If Windows, I would ctrl-alt-del and terminate the process.  How do I do that in Ubuntu 9.1?


Thanks,

---

### Post by philinux on 2009-11-09
Right click on the top panel and add the applet Force Quit.

Also on Edit>prefs if its firefox on the Main tab, if you got the option show my windows and tabs from last time, thats why it comes up.

---

### Post by XCan on 2009-11-09
The closest thing to the ctrl+alt+del equivalent app in linux is probably the System Monitor. Add it to your upper panel, Right click -> Add to panel -> System Monitor.

---

### Post by whoop on 2009-11-09
ps -A | grep firefox
kill -9 <firefox's PID>

---

### Post by wojox on 2009-11-09
```
killall firefox
```

---

### Post by original_jamingrit on 2009-11-09
my favourite way is to use xkill.

Press Alt-F4 for the run dialog, enter ```
xkill
``` and then left-click on the thing you want to kill.  Right-click to cancel.

---

### Post by RobinJ1995 on 2009-11-09
> **original_jamingrit said:**
> my favourite way is to use xkill.

Press Alt-F4 for the run dialog, enter ```
xkill
``` and then left-click on the thing you want to kill.  Right-click to cancel.
*alt+F2*

---

