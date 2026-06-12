---
title: "Closing laptop lid shuts down second display"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by Iateabee on 2011-02-12
_Info_
Ubuntu 10.10
IBM R51 laptop
Ubuntu screen mode: LCD (laptop) off, secondary display on
Function keys: same as above:
power utility: screen closed option = blank (I do not have a "do nothing option" only suspend, hibernate, and blank)

_Problem:_
When have everything in the above state with the laptop lid open all is fine.  The laptop screen is blank and the sec display is on and in the correct resolution.  As soon as I shut the lid the sec display goes blank.


I saw another Ubuntu user with a power utility that had a "do nothing" option under lid close.

---

### Post by mr_luksom on 2011-02-12
When I solved this for my setup, used gconf-editor and manually typed 'nothing'.

See this thread: [http://ubuntuforums.org/showthread.php?t=1293379](http://ubuntuforums.org/showthread.php?t=1293379)

---

### Post by Iateabee on 2011-02-13
Thanks - I applied the fix rebooted and this worked.  Although it didn't add the "do nothing option"  to my Power Management program as it mentioned.  I can live with that.

---

### Post by mr_luksom on 2011-02-13
Great to hear. Don't forget to mark the thread as solved.

---

