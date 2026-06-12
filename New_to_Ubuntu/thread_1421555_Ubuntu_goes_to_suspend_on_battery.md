---
title: "Ubuntu goes to suspend on battery"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-03-04
This isn't a huge deal, but everytime I when I put my computer into suspend, then unplug it to take to class, then open it up, the computer will come out of suspend and show my login screen for about 2 seconds, then it immediately goes back into suspend mode. It makes no sense and for some reason, just started doing this. Like I said, its not a big problem, but it is extremely annoying. Has anyone else had this problem?

---

### Post by Kulgan on 2010-03-05
Does it ever wake up? I have to hard reboot after hibernating/suspending. This a problem that has bugged me in Linux for a long time. It worked in Jaunty but no longer... 

This is on a Dell Studio 1537.

---

### Post by wilee-nilee on 2010-03-05
With my acer aspire netbook if you unplugged the power in Ubuntu it shutdown. I had to change the power buttons in gconf-editor, so check to see if it is a unplug that is the culprit here. So I have the lid_ac set to do nothing and lid_battery do nothing. This was a fix I came across for this computer model

You can edit and check the status with alt-f2 then run gconf-editor go to apps-gnome power manager-buttons.

---

### Post by Kulgan on 2010-03-05
Or System &#8594; Preferences &#8594; Power Management

---

### Post by wilee-nilee on 2010-03-05
> **Kulgan said:**
> Or System &#8594; Preferences &#8594; Power Management

Karmic doesn't have do nothing for lid closing.

---

### Post by Kulgan on 2010-03-05
Indeed it does not. It has "Blank Screen" instead. Fortunately unblanking the screen does not cause problems.

---

