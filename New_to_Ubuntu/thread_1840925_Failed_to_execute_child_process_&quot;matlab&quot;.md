---
title: "Failed to execute child process &quot;matlab&quot; (Permission denied)"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by thewasteland on 2011-09-08
Yeah, basically the title says it all. I just installed MATLAB, made a launcher for it (all by blindly following instructions from the internet, so don't go thinking I have any sort of skill with Ubuntu), and now I can't open it - I keep on getting "Could not launch "MATLAB R2011a": Failed to execute child process "matlab" (Permission denied)" whenever I try to open it. Any help would be appreciated. Thanks.

---

### Post by ubudog on 2011-09-08
Try this:
Right click on the launcher, select Properties, then add: 

```
gksu 
``` 

at the beginning of the "Command" text field, with a space after the u in gksu.

Then, click the Close button, and try to launch it.  It will ask you for your password, because apparently matlab needs root privileges (it cannot be run by your regular user account).

---

