---
title: "to disable f1"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by macanudokiosko on 2009-09-18
Is there any practical way for disabling the f1 key, which can get annoying sometimes?

---

### Post by kerry_s on 2009-09-18
[http://www.ehow.com/how_2180748_command-linux-swap-keyboard-keys.html](http://www.ehow.com/how_2180748_command-linux-swap-keyboard-keys.html)

i suppose you could just leave it blank to disable?

---

### Post by macanudokiosko on 2009-09-18
ok, tx...  
> **kerry_s said:**
> [http://www.ehow.com/how_2180748_command-linux-swap-keyboard-keys.html](http://www.ehow.com/how_2180748_command-linux-swap-keyboard-keys.html)

i suppose you could just leave it blank to disable?

---

### Post by falconindy on 2009-09-18
You could also go into "System -> Preferences -> Keyboard Shortcuts" and make a new shortcut that does something like `echo nothing > /dev/null` and then bind that to F1.

edit: which upon testing, doesn't actually disable it... sweet! xmodmap, go! keep in mind that'll likely disable ALL functionality for the F1 button, not just prevent you from getting a help window.

---

### Post by macanudokiosko on 2009-09-18
yeah, i'd tried it about two months ago... the other method of this post seems great, yet a bit radical... I'm about doing it nonetheless. 
 > **falconindy said:**
> You could also go into &quot;System -> Preferences -> Keyboard Shortcuts&quot; and make a new shortcut that does something like `echo nothing > /dev/null` and then bind that to F1.

edit: which upon testing, doesn't actually disable it... sweet! xmodmap, go! keep in mind that'll likely disable ALL functionality for the F1 button, not just prevent you from getting a help window.

---

### Post by kerry_s on 2009-09-18
nevermind

---

### Post by kerry_s on 2009-09-18
i found the command in gconf-editor, but if you disable it, you get a error pop up instead, i can live with that it's fast & easy to close.

---

