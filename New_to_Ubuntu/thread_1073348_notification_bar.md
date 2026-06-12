---
title: "notification bar"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by computerfreak on 2009-02-18
i feel really dumb right now putting a forum in the beginners because i've used ubuntu for almost 2 years, but i need to fix my notification bar so i can see my wireless network. and i think that its gone it wont even hook up automatically like it always does. can some please help. I'll be forced to use windows if i don't get help

---

### Post by computerfreak on 2009-02-18
i also tried running another notification bar but it was empty and when i ran tranmission i saw the icon.

---

### Post by 3rdalbum on 2009-02-18
There are two possible causes:

1. You've somehow removed the Notification Area from your panel.

2. The Network Manager applet is not starting up.

Fixing the first is easy - just right-click your panel and "Add to Panel..." then add the Notification Area. **EDIT: You've just said that you've tried this already. Kept this part of the post to help others who might have the same problem**

Fixing the second is easy too. Press Alt-F2 and type "nm-applet" and press Enter. Add the command to your Startup Items in System > Preferences > Sessions if it doesn't reappear after reboot.

On some occasions, the Network Manager applet won't appear because it can't communicate with HAL. If this happens, just run "sudo hald" and your Network Manager should work again.

---

### Post by computerfreak on 2009-02-18
ill try it right now

---

### Post by computerfreak on 2009-02-18
its working now. i rebooted the computer before i put up the post went down to use a windows computer and i went up to use your solutions and i just logged in. thanks for the responses anyway!!:D

---

