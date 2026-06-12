---
title: "Exit fullscreen in Remote Desktop Viewer"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by RealG187 on 2009-02-20
How do I exit full screen in remote desktop viewer? I press CTRL ALT ENTER but it just goes back to it.

---

### Post by RealG187 on 2009-02-24
[http://adminian.com/2008/03/18/fix-rdesktop-exit-fullscreen-issue-in-ubuntu/](http://adminian.com/2008/03/18/fix-rdesktop-exit-fullscreen-issue-in-ubuntu/)

> Utility > Workarounds > uncheck Legacy Fullscreen Support
That seems to have fixed it, I can use CTRL+ALT+Enter...

---

### Post by DiscoKiller on 2009-03-21
i`ve found hitting ctrl+alt a couple of times until the grey bar appears at the top of the screen then hittin F11 will do the trick

peace 

DK

---

### Post by current@dabb.no on 2010-09-23
This solved the problem for me. 

Un check the "Hide window manager's decorations" under the Performance tab on the RDP client

---

### Post by jcoles on 2011-11-12
This problem is also present in Oneiric (11.10). 

After installing compizconfig-settings-manager, I discovered that "Legacy Fullscreen Support" was already disabled, but the problem was still there. 

After disabling/re-enabling Workarounds and doing a reboot, Ctrl-Alt-Enter correctly switches between full screen and maximized window. 

I'm not sure which of these actions actually did the trick.

---

### Post by Pourounas on 2012-01-25
Ctr+Alt+Enter worked for me on 10.04 LTS

---

### Post by frogger78 on 2012-02-19
> **jcoles said:**
> This problem is also present in Oneiric (11.10). 

After installing compizconfig-settings-manager, I discovered that "Legacy Fullscreen Support" was already disabled, but the problem was still there. 

After disabling/re-enabling Workarounds and doing a reboot, Ctrl-Alt-Enter correctly switches between full screen and maximized window. 

I'm not sure which of these actions actually did the trick.

Holding CNTL and mousing to the top-center of the screen revealed a menu where you can diable full screen.

---

### Post by kloing on 2013-03-07
It works fine for me using 12.04 LTS.

---

### Post by sandyd on 2013-03-07
**Necromancing - thread closed**
Please do not post in threads more than one year old.

Thanks!

---

