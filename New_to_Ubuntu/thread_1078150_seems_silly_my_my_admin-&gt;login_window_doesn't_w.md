---
title: "seems silly my my admin-&gt;login window doesn't work"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by systemchris on 2009-02-23
i wanted to enable auto-logon for my only account for ubuntu on my desktop but when i select admin->login window it appears then suddenly disappears

otherwise my installation seems to work fine im thinking it's either a desktop issue or just that aspect of the OS :s

any idea what i can do

in the system log i saw this:
Feb 23 06:55:57 morch-ubuntu kernel: [  423.041986] gdmsetup[6209]: segfault at 8 rip 7f69dfa9f3e3 rsp 7fffeeb3a410 error 4

---

### Post by blazemore on 2009-02-23
Find out the actual command that is run when you click the icon.
Right-click on the menu, do Edit Menus

Browse to the Login Windows entry, then click edit.
Copy the content of the "command" field

Open a terminal, and paste this command in.
Then when it crashes, you'll be able to see any program-specific errors.

---

### Post by geirha on 2009-02-23
gdmsetup is segfaulting, that's not right. What Ubuntu release are you running, and which version of gdm?
```
lsb_release -ds
LANG=C aptitude show gdm|grep ^Version

```

---

### Post by systemchris on 2009-02-23
> **geirha said:**
> gdmsetup is segfaulting, that's not right. What Ubuntu release are you running, and which version of gdm?
```
lsb_release -ds
LANG=C aptitude show gdm|grep ^Version

```

just tried to load gdmsetup from the terminal using the command from admin>login window and got this

gdmsetup[6073]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[6073]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[6073]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)


this is from a UBUNTU 8.04.2 fresh install and gdm is  2.20.7-0ubuntu1.1



from looking even harder on the internet, i found that it is a reproducible bug, and only seems to occur if you have a blank CD in the computer lol very random indeed

---

