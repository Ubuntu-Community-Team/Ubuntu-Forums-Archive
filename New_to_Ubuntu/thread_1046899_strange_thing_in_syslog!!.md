---
title: "strange thing in syslog?!?!"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Alden born on 2009-01-21
well I check the syslog and I keep getting this error in the log 

> Dec  9 14:42:15 paul-laptop kernel: [  325.532829] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Dec  9 14:42:15 paul-laptop kernel: [  325.542866] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
Dec  9 14:42:15 paul-laptop kernel: [  325.542879] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.

it just keeps adding its self in the log.

thanks.

---

### Post by mjheagle8 on 2009-01-21
you're pressing a key the computer doesnt recognize.

---

### Post by Alden born on 2009-01-21
> **mjheagle8 said:**
> you're pressing a key the computer doesnt recognize.

see thats what i think it is but I'm not pressing any keys. it also show up when the computer is booting because i took the splash screen off to were its just text. But I'm not pressing anything and no keys are stuck as well.

---

### Post by rustutzman on 2009-01-21
I found this in the archives:

snowflake
October 18th, 2005, 12:04 PM
Hi, 

I had the same problem. I found a script, called hotkey-setup in init.d, which is started every boot. I stopped this program and now it's working properly, there isn't any errors in logs.

---

