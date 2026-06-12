---
title: "Ubuntu Tweaks tweaked Ubuntu... permanently"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by jermza on 2011-01-13
After a few days of testing it, I removed Ubuntu Tweaks.

But the tweaks have remained even AFTER the program was removed.  Why is this?  And how can I revert the tweaks?

---

### Post by mastablasta on 2011-01-13
ubuntu tweak is only a graphics interface. the easiest way would be to remove them through ubuntu tweaks.
 
to do it without that, you would first need to say exactly what tweaks did you make.

---

### Post by mikewhatever on 2011-01-13
Why do you want the tweaks removed? You've applied them, right?

---

### Post by jermza on 2011-01-13
> **mikewhatever said:**
> Why do you want the tweaks removed? You've applied them, right?
I've applied them, yes, but I thought that they would be reverted if the program is removed.  That's kind of like uninstalling a theme but the theme remains.

---

### Post by mikewhatever on 2011-01-13
> **jermza said:**
> I've applied them, yes, but I thought that they would be reverted if the program is removed.  That's kind of like uninstalling a theme but the theme remains.

Well, Ubuntu-Tweak tweaks the settings, and when removed, the settings remain. Makes sense to me. :D

---

### Post by Frogs Hair on 2011-01-13
Ubutu Tweak is a configuration editor / Compiz short cut in some cases , so the changes remain after removal.

---

### Post by hansolo4949 on 2011-01-13
You should reinstall Ubuntu tweak, and manually undo every one of the tweaks you applied. It might take awhile, but it should work.


hansolo4949

---

### Post by rburkartjo on 2011-01-13
what hans said will work had to do the same thing awhile ago

---

### Post by ExileAmongYou on 2011-01-13
> **jermza said:**
> I've applied them, yes, but I thought that they would be reverted if the program is removed.  That's kind of like uninstalling a theme but the theme remains.

Ubuntu Tweak is just a user-friendly interface that does tricky settings changes for you. You *could* do all the things it does by editing config files or by using things like gconf-editor, all those options are hidden away in settings files somewhere. Ubuntu Tweak changes those settings files, so they stay changed when you uninstall.

---

### Post by jermza on 2011-01-14
> **ExileAmongYou said:**
> Ubuntu Tweak is just a user-friendly interface that does tricky settings changes for you. You *could* do all the things it does by editing config files or by using things like gconf-editor, all those options are hidden away in settings files somewhere. Ubuntu Tweak changes those settings files, so they stay changed when you uninstall.
Okay, I understand now.  Thanks.

I've been using Ubuntu (with no dual boot) for a month now, and every day I learn how different it is to Windows.  :D

---

### Post by mastablasta on 2011-01-14
> **jermza said:**
>  
I've been using Ubuntu (with no dual boot) for a month now, and every day I learn how different it is to Windows. :D
 
 
actually if you ever used a utility called TweakUI in Windows (now available on Microsoft pages i believe) you would get similar result. You would tweak set up files and when you uninstall it (or i think just delete it) the changes you made would remain in the registry and any star up config files (config.sys, autoexec.bat...).

---

