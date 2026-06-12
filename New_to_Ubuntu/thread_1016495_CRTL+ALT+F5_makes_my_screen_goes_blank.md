---
title: "CRTL+ALT+F5 makes my screen goes blank"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-20
what exactly does CRTL+ALT+F5 do? I couldn't recover from it.

please, save your work before doing this command.

---

### Post by namdung on 2008-12-20
> **shiningkenmonster said:**
> what exactly does CRTL+ALT+F5 do? I couldn't recover from it.

please, save your work before doing this command.

Ctrl + Alt + F7 should bring you back to GNOME.

---

### Post by zman58 on 2008-12-20
Unlike Windows, Linux is a true concurrent multi-user system.

CTRL-ALT-F5 takes you to tty5. This is a text console input.output screen which allows you to log in and run in text mode. There are other tty consoles also found at F1,F2,F3,F4 and the one you found at F5, and then F6. Other output screens are reserved for graphical output which are F7 thru F12. The first graphical login screen by default resides at CTRL-ALT-F7. If another X (graphical) user logs onto the local computer at the same time, then they will be at CTRL-ALT-F8.

---

### Post by doas777 on 2008-12-20
you should see a text interface. do you?
xman explained it pretty well. if you don't see a text login prompt however, there may be somthing wrong with your VGA settings (not your normal video card settings, but the res settings for non-graphical screens)

but then again, if you never plan to use the VTYs then theres little point in worrying about it. just CA+ F7 to return to yoru desktop.

have fun,
franklin

---

### Post by HuaiDan on 2011-06-24
Actually, only alt-f7 is necessary to bring you back. Way to resurrect a dead thread, I know, but I was searching for a way to make this feature return to a password prompt. It would be a cool keyboard/screen lock feature if it were only password protected. Right now I can use it at home, no one would know about alt-f7. It's a nice panic button, as it allows you to "return" to any safe sessions.

So, is there any way to make alt-f7 return a password prompt?

---

