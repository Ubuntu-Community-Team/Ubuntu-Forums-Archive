---
title: "Change autologin options without running gdmsetup?"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by lsp432 on 2009-09-12
I have a user set to autologin to my xubuntu box, which I'm pretty sure I enabled using gdmsetup. Now I need to turn that autologin off, but I can't run gdmsetup because I'm SSHing into the computer, and X11 forwarding isn't working (I'll deal with that later). /etc/gdm/gdm.conf says AutomaticLoginEnable=false, and /etc/gdm/gdm.conf-custom doesn't have an autologin-related entry, so I'm looking for whatever file is actually holding the settings that make my user automatically login, and how I can change these settings to disable the autologin.

Thanks!

---

### Post by kerry_s on 2009-09-12
it is /etc/gdm/gdm.conf, did you restart gdm after making the changes?

**sudo /etc/init.d/gdm restart**

---

### Post by lsp432 on 2009-09-12
d'oh, I guess sometimes I overlook the simple things, thanks a lot for the help!

---

