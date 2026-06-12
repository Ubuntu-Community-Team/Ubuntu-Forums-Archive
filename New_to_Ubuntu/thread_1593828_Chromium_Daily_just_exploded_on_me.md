---
title: "Chromium Daily just exploded on me"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-10-11
Hi all. I have a bit of an annoying question.

I run the daily builds of Chromium, (and although I know they are prone to breakage) Ive been experiencing a problem that has never occurred for me before.

My current session will not load any websites properly. It will not show proper CSS, nor will it display images. 

Normally when something breaks in a daily build, its fixed the next day or soon after. Ive been experiencing this problem for nearly 4 days now.

On the forums here, I could roughly make out the pages, but again- no images or the links associated with them will appear.

Ill attach a screencap of Youtube's homepage to explain what EVERY site looks like to me..



Does anyone else experience this problem? What could I do to resolve the problem?

MORE INFO:
I just installed regular Google Chrome, and there are no problems there. It seems that the problem is isolated to Chromium only.

---

### Post by tgalati4 on 2010-10-11
Perhaps your cache is corrupted.  Try a clean install of chromium and see if the problem goes away.

---

### Post by tom.swartz07 on 2010-10-12
Tried uninstalling and reinstalling. No dice.
I should clarify. It loads the page properly, but once everything is finished (IE, all of the items on the page have been received by my computer and the browser is no longer transferring files, etc) It takes a dump and goes to the version of the page you see above.

Chromium daily works great on my other computer, and Google Chrome on the affected computer works as well- which is what has me confused.

---

### Post by xircon on 2010-10-12
No problems here - 8.0.552.0 (62225) Ubuntu 10.10

Steve

---

### Post by tom.swartz07 on 2010-10-12
> **xircon said:**
> No problems here - 8.0.552.0 (62225) Ubuntu 10.10

Steve

Thats the one that Im running.


Okie dokie guys.
Im just going to wipe and install 10.10 anyway. Ill confirm or deny that the problem still exists after that.


Thanks for the help!

---

### Post by xircon on 2010-10-12
Try uninstalling and purging first, then delete all references to chromium in your home directory /home/you/.config/chromium

---

### Post by tom.swartz07 on 2010-10-12
> **xircon said:**
> Try uninstalling and purging first, then delete all references to chromium in your home directory /home/you/.config/chromium

Holy Crap.

Clearing the .config/chromium folder fixed it!

Whatever it was, that fixed it!

---

### Post by xircon on 2010-10-12
Glad it worked!

---

