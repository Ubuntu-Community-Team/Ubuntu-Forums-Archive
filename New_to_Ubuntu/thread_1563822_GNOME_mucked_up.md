---
title: "GNOME mucked up"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by fslezak on 2010-08-29
Hello.

I recently installed Sugar (just to see what it does), and my GNOME is mucked up now.

I PURGED Sugar after these issues started:


[LIST]
[*]The panel did not activate AT ALL, I needed to run the panel from terminal, and there was this output: ```

** (gnome-panel:7914): WARNING **: Unable to parse mouse modifier 'disabled'

Unable to open desktop file 400095002695?cmd=ViewItem&pt=Video_Games_Games&hash=item5d27854047
.desktop for panel launcher
```
[/LIST]

[LIST]
[*]The mouse barely worked, left-click moved windows (even on buttons), right click was not affected. (only in standard* GNOME)
[/LIST]
PLEASE HELP ME!!!

---

### Post by blazemore on 2010-08-29
If you have access to a terminal, you can restore Gnome's default settings by running the following command:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

