---
title: "Avant Window Navigator"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by winstont11 on 2009-09-08
Hello, I'm attempting to access avant window navigator through applications - accessories, however, I keep getting this error message:
"Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

So I ran this in the terminal: compiz (-fusion)
bash: syntax error near unexpected token `-fusion'

So then I ran compiz fusion
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3c0002c specified for 0x3c00034 (Starting a).

I'm not sure what I'm suppose to be doing.

Thanks for the help!

---

### Post by dearingj on 2009-09-08
Go to System->Administration->Hardware Drivers and make sure that you've got drivers for your graphics card installed (if the drivers are listed), then do System->Preferences->Appearance and try to enable visual effects.

---

