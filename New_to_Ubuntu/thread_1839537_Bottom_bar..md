---
title: "Bottom bar."
date: 2011-09-05
forum: New to Ubuntu
---

### Post by v.mccann on 2011-09-05
Hi all, 

I did a search and didn't find anything similar. The bottom task bar has disappeared from my desktop and I can't figure out how to bring it back. Any thoughts? Sorry not knowing how to more accurately describe the problem.

---

### Post by Rex Bouwense on 2011-09-05
What version are you using?

---

### Post by westie457 on 2011-09-05
> **v.mccann said:**
> Hi all, 

I did a search and didn't find anything similar. The bottom task bar has disappeared from my desktop and I can't figure out how to bring it back. Any thoughts? Sorry not knowing how to more accurately describe the problem.

open a terminal type this in ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by IWantFroyo on 2011-09-05
Look here: [http://ma65p.wordpress.com/2008/06/23/how-to-restore-the-original-panel-and-menu-bar-in-ubuntu/](http://ma65p.wordpress.com/2008/06/23/how-to-restore-the-original-panel-and-menu-bar-in-ubuntu/)

I can confirm it works in 10.04.

---

### Post by v.mccann on 2011-09-05
Rex,

I'm using 11.04. Sorry, I should have known to post that.

Westie, 

I get: gnome-panel: no process found

Froyo, no effect. I tried restarting. 

Thanks for the responses.

---

### Post by IWantFroyo on 2011-09-05
What happens when you run:
```
gnome-panel
```
And follow the method.

I assume you are using Gnome Classic/Fallback.

PS- Opening terminal by keyboard is ctrl-alt-t

---

### Post by westie457 on 2011-09-05
If you are using the Unity interface I think the command is ```
unity --reset
```

You might need to remove one of the '-' for it to work. Not 100% sure as I am using an older version.

---

### Post by v.mccann on 2011-09-05
> **IWantFroyo said:**
> What happens when you run:
```
gnome-panel
```And follow the method.

I assume you are using Gnome Classic/Fallback.

PS- Opening terminal by keyboard is ctrl-alt-t


Thanks, that did it - which is good, because I don't know the answer to your next question.

Thanks everyone.

---

### Post by ubun2geek on 2011-09-05
Please mark the thread as solved.

---

### Post by ubun2geek on 2011-09-05
This may also be useful:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

