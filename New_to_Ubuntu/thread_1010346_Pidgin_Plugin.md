---
title: "Pidgin Plugin?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by insub2 on 2008-12-13
Does anybody know of a way to have all Pidgin chat windows always "Always on Visible Workspace"?

---

### Post by JKBurton on 2008-12-13
If you're using Compiz to manage your windows, then yes.

[http://ubuntuforums.org/showthread.php?t=665775]("http://ubuntuforums.org/showthread.php?t=665775")

Install the Compiz Config Settings Manager, if necessary. You run it from the System/Preferences menu. 

Put a checkmark beside "Regex Matching" tool under "Utility", if it isn't already.  

Then down in "Window Management", open "Window Rules". Check "Enable Window Rules" on the left side. On the right side, beside "Sticky", enter "class=Pidgin & !title=Buddy List" without the quotes. Press the "Back" button to leave that dialog, and close the Settings Manager.

Note it doesn't take effect until you logout/login. I didn't realize that and wasted time trying to figure out what I was doing wrong :)

Good idea, incidentally. I'd never thought of doing this for myself, but I like it!

---

