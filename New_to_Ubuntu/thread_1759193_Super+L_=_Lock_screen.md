---
title: "Super+L = Lock screen"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by jrsutton on 2011-05-15
I cannot figure out what I'm doing wrong. I want to set a keyboard shortcut for lock screen as "Windows Key"+l. When I set this in the keyboard shortcuts it does nothing. Setting it back to default of Ctrl+Alt+L works.

---

### Post by Johnley on 2011-05-15
I set it to control+L.

Close enough :P

---

### Post by SecretCode on 2011-05-15
What version of Ubuntu? Are you using Unity? - I believe Unity takes over all WinKey combinations.

---

### Post by jrsutton on 2011-05-15
Ah, I am using 11.04 with Unity. And I can only see where to edit keyboard shortcuts, not add additional ones in Unity.

---

### Post by SecretCode on 2011-05-16
Might be worth installing compizconfig-settings-manager. Some of the plugins allow setting of keyboard shortcuts for various functions, including arbitrary commands. (You'd need to find out the command that locks the screen.)

---

### Post by jrsutton on 2011-05-19
After posting and reading feed back from this thread that is precisely what I did. That I can find in the general config, Unity config portions, or anywhere else in the CCSM there is not a standard (default) lockscreen keyboard shortcut. This appears to be still controlled by the normal keyboard shortcut program, and from what I can tell it does not support the super key. :confused:

---

### Post by SecretCode on 2011-05-19
No, I didn't think there was, but you can use the general commands plugin and map Super-L to an arbitrary command line, which may be something like
```
gnome-screensaver-command --lock
```

---

### Post by wildmanne39 on 2011-05-19
> **jrsutton said:**
> I cannot figure out what I'm doing wrong. I want to set a keyboard shortcut for lock screen as "Windows Key"+l. When I set this in the keyboard shortcuts it does nothing. Setting it back to default of Ctrl+Alt+L works.
Hi, here is a background with all the unity shortcuts already, and if you look below this text in my signature there is a guide that has how to setup shortcuts, and many other useful things as well.

---

