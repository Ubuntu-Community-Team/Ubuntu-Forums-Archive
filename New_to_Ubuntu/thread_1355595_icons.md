---
title: "icons"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by garage jack on 2009-12-15
hi guys. it s seems there is something wrong with my appearance menu. sometimes, without any explainable reason my icons change appearance, and when i try to change them back whole thing looks even stranger, for example, there is a color from one theme, windows border from another and icons from another theme. when i try to change appearance of my mouse pointer, for example to white glass , it is white glass on web page, but on ubuntu desktop it has its  default appearance. and my notification area in upper right corner , where is volume control and network connection, got messy too, icons change appearance when i log in and wnc icon is blocked. can someone help me with this? thanks

---

### Post by HarrisonNapper on 2009-12-17
Do you have a particular theme you've installed, are you running compiz, or is there anything you've configured about your desktop that isn't in the default installation?

---

### Post by garage jack on 2009-12-17
> Do you have a particular theme you've installed, are you running compiz, or is there anything you've configured about your desktop that isn't in the default installation?

yes, i run compiz, theme is standard, human i think ( orange one, pretty standard) and i run default installation, no emerald or something like that. compiz is set to normal

---

### Post by HarrisonNapper on 2009-12-17
Human is the default theme, so no worries there. Wouldn't surprise me if it's compiz. System>Preferences>Startup Applications and uncheck compiz then restart or kill X and login again. See if that fixes the strangeness. If it does, it's a compiz setting somewhere, but if not, it's probably gnome-panel.

---

### Post by garage jack on 2009-12-17
i don't know what X is, sorry. btw, my login tune sounds kind of strange, those percussion sounds are skipping a little, do you think that has to do with compiz, too? should i uncheck some gnome settings from startup applications too? if so, which? thanks

---

### Post by HarrisonNapper on 2009-12-17
No. Only uncheck compiz. Don't worry about the kill X thing if you don't know what it is. You can enable Ctrl-Alt-Backspace to hard restart X and take you back to your login screen, but it can and will cause data loss. If you're comfortable with remembering that, you can enable it in System>Preferences>Keyboard>Layouts. Otherwise, just reboot or logout/login after disabling compiz on startup. Don't know about the sounds yet.

---

