---
title: "Login window problem"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-01-31
I have been playing around with customizing my login window with various GDM themes... Some of them I have changed the code and design and they worked fine but suddenly I don't have the option to turn off/reboot/suspend my computer at the login screen (only change sessions and languages are still there). 

I changed back to the default login windows but the problem is still there. I only changed the .xml and graphic files from the downloaded GDM themes and didn't change any other options.

Any thoughts of where the problem could be from? And how could I fix it to get these options back?

Thanks!

---

### Post by -kg- on 2009-01-31
Try this:  Click "System/Administration/Login Window."  Click on the "Local" tab.  At the bottom of the window, make sure "Show Actions Menu" is checked.  My sub item (Include Hostname Chooser) is checked, as well.

---

### Post by sylvainrb on 2009-01-31
Haha I guess that was it... Thank you! I don't remember checking it off though. Do you think it could have been checked off by modifying the GDM themes? (I don't...)

---

### Post by -kg- on 2009-02-01
> **sylvainrb said:**
> Haha I guess that was it... Thank you! I don't remember checking it off though. Do you think it could have been checked off by modifying the GDM themes? (I don't...)

Possibly.  I don't really know what I did to effect that change myself.  I just remember that it happened to me quite a while back, and that was the solution suggested to me that worked.

---

