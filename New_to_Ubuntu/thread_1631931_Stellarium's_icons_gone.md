---
title: "Stellarium's icons gone"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by CaptainJamie on 2010-11-27
I have a screen shot of the problem because I'm not sure how to describe  it. Also I have had difficulty searching for the problem because I  always find " no desktop icon" and this is not the same problem. I would  be grateful of any assistance.[IMG]file:///home/jamie/Desktop/Screenshot.png[/IMG]

---

### Post by daggerstab on 2010-11-27
Could you please try opening a terminal and trying to start Stellarium with:
```
stellarium --safe-mode
```

---

### Post by CaptainJamie on 2010-11-27
That was impressive. It worked. But I have to do that every time, as opening it normally doesn't have icons still. But thanks for that!

---

### Post by marin123 on 2010-11-27
> **CaptainJamie said:**
> That was impressive. It worked. But I have to do that every time, as opening it normally doesn't have icons still. But thanks for that!

if stellarium runs on startup, simply add startup apps entry "stellarium --safe-mode" and uncheck regular stellarium startup.

System -> Preferences -> Startup applications

---

### Post by daggerstab on 2010-11-28
I can't imagine a possible reason for making Stellarium a start-up application.

**CaptainJamie**, you can edit the command used by the icon in the applications menu.

[LIST]
[*]Go to System -> Preferences -> Main Menu.
[*]In the menu editor, find the "Stellarium" entry.
[*]Select it and press the "Properties" button.
[*]In the "Launcher properties" window, change the "Command" field from "stellarium" to "stellarium --safe-mode".
[*]Close the window and the menu editor. Voilá! The launcher in the menu should start Stellarium in safe mode now.
[/LIST]

---

### Post by CaptainJamie on 2010-11-28
Thanks very much! Although the problem isn't fixed it is certainly a perfectly good workaround. I think I might be getting the hang of Linux... With a little help now and then!

---

