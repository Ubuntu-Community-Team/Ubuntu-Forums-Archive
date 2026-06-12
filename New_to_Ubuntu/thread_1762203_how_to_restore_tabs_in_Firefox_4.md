---
title: "how to restore tabs in Firefox 4?"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by fidamehran on 2011-05-18
Is it possible to restore (or Save, in the first place) the tabs in Firefox 4 in Natty?
In Windows, it also does not ask to save tabs. But gives the chance to restore the tabs at next startup.

---

### Post by rosencrantz on 2011-05-18
FF4 probably saves the current state every time you quit without asking. You can restore the previous settings by default in the preferences window (Edit->Preferences), see the attached screenshot. Alternatively, there is the History->Restore previous session menu entry.

---

### Post by lovinglinux on 2011-05-18
Get [Session Manager]("https://addons.mozilla.org/en-US/firefox/addon/session-manager/") extension. It allows to save any number of different sessions, with their own set of tabs. It also remembers windows positions/sizes and which sidebar you was using.

---

### Post by fidamehran on 2011-05-19
Thanks. I guess, this'll do.

---

### Post by blackplague1347 on 2011-05-19
If you want FF4 to ask you to save your currently-open tabs when you close it (as Firefox did in versions prior to 4.0), you can do that. 

1) In the address bar type "about:config" 
2) Click "I'll be careful, I promise"
3) In the "filter" box, type "showquit"; the list should be reduced to one item that says: "browser.showQuitWarning"
4) Change the value of browser.showQuitWarning from "false" to "true" (right-click it and select "toggle" to change it from "false" to "true" and vice-versa

I'm not sure if that's what you meant with this thread, but there it is.

---

### Post by fidamehran on 2011-05-19
> **blackplague1347 said:**
> If you want FF4 to ask you to save your currently-open tabs when you close it (as Firefox did in versions prior to 4.0), you can do that. 

1) In the address bar type "about:config" 
2) Click "I'll be careful, I promise"
3) In the "filter" box, type "showquit"; the list should be reduced to one item that says: "browser.showQuitWarning"
4) Change the value of browser.showQuitWarning from "false" to "true" (right-click it and select "toggle" to change it from "false" to "true" and vice-versa

I'm not sure if that's what you meant with this thread, but there it is.

Gee, Thanks !!! This was the ultimate solution. And official one too..... :P

---

### Post by lovinglinux on 2011-05-19
> **fidamehran said:**
> Gee, Thanks !!! This was the ultimate solution. And official one too..... :P

Indeed that is the built-in method. However, I recommend that you give Session Manager extension a try. It is awesome. You can use it for example to create specific sessions for specific tasks. This helps keeping the number of open tabs under control.

---

### Post by fidamehran on 2011-05-19
> **lovinglinux said:**
> Indeed that is the built-in method. However, I recommend that you give Session Manager extension a try. It is awesome. You can use it for example to create specific sessions for specific tasks. This helps keeping the number of open tabs under control.

Thanks. Installed that too.... :guitar:

---

