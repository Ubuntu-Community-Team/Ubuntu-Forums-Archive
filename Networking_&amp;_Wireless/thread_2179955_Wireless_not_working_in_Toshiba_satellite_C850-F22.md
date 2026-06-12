---
title: "Wireless not working in Toshiba satellite C850-F22T"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by Eric_Ouma_Jobunga on 2013-10-10
I have installed Ubuntu and Windows 7. Wireless works perfectly well with Windows 7 but not ubuntu in my laptop. I have tried following the suggested Dropbox link but unfortunately the configuration never worked. I need some advice to fix the problem.

---

### Post by varunendra on 2013-10-11
Welcome to the forums Eric !:)

> **Eric_Ouma_Jobunga said:**
> I have tried following the suggested Dropbox link but unfortunately the configuration never worked. I need some advice to fix the problem.
What dropbox link? Do you mean "wireless_script" suggested by Wild Man? If so, it is not a fix, it just collects some info that helps us to suggest you a fix. You can follow the "Wireless Script" link in my signature to see detailed instructions.

If having trouble with it, just open a terminal (Ctrl-Alt-T) and enter these commands in it (one by one, you may copy-paste these) -
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
rfkill list all
```
Post back the whole output of the above commands.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

